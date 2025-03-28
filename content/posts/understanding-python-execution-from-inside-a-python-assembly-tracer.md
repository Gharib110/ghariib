---
title: "Understanding Python execution from inside: A Python assembly tracer"
date: 2025-01-19
categories: 
  - "cybersecurity"
  - "cybersecurity-awareness"
  - "security"
  - "security-awareness"
  - "vulnerabilities"
tags: 
  - "define"
---

Lately, I have been looking at the Python's execution model. I was curious about the implementation of some opcodes like `YIELD_VALUE` and `YIELD_FROM`, how were compiled list comprehensions, generator expressions and other fun Python features, and what happens at the bytecode level when exceptions were raised. Reading the `CPython` code is really instructive, but I was feeling like something was missing to fully understand the bytecode execution and the stack evolution. Yeah, `GDB` is cool but I'm a lazy guy who wanted a high-level interface and code some Python.

So my goal was to create a bytecode-level tracing API like the one offered by sys.settrace but with a finer granularity. This exercise was perfect to practice my C-into-Python coding.

What we are going to need is:

- A new opcode in the `CPython` interpreter
- A way to inject the opcode in Python bytecode
- Some Python code to handle the opcode on the Python side

_In this article everything is based on Python3.5_.

## A new opcode for CPython

### Our new opcode: `DEBUG_OP`

This new opcode, that I will call `DEBUG_OP`, is my first try at writing C code for CPython. I tried to keep it as simple as I could.

What we want is a way to call some Python code whenever our opcode is executed. We also want to be able to retrieve some data about our execution context. Our opcode will pass it as parameters to our callback. The useful information I identified is:

- The content of the stack
- The frame object that executed `DEBUG_OP`

So all our `DEBUG_OP` needs to do is:

- Find the callback
- Create a list with the content of the stack
- Call the callback with that list and the current frame as parameters

Sounds easy! So let's go!

**Disclaimer**: the following explanations and code are the result of a LOT of segfaults.

First thing to do is to give a name and a value to our opcode. For that, we need to go into `Include/opcode.h`

```
::c
/** My own comments begin by '**' **/
/** From: Includes/opcode.h **/

/* Instruction opcodes for compiled code */

/** We just have to define our opcode with a free value
    0 was the first one I found **/
#define DEBUG_OP                0

#define POP_TOP                 1
#define ROT_TWO                 2
#define ROT_THREE               3
```

The easy part is done. Now we have to actually code our opcode behaviour.

### Implementing `DEBUG_OP`

First question we need to ask ourself before even thinking about the implementation of `DEBUG_OP` is "_What my interface is going to be?_".

It's cool to have a shiny new opcode that calls some code but what code is it going to call exactly? How will it retrieve the callback function? I chose what looked like the simplest solution: a fixed name function in the frame globals.

The question is: "_how do I look for a fixed C-string in a dict?_"

To answer this question we can look at some fixed identifiers used in the Python main loop: the ones associated with context managers `__enter__` and `__exit__`.

We see that it's used in the `SETUP_WITH` opcode:

```
/** From: Python/ceval.c **/
TARGET(SETUP_WITH) {
_Py_IDENTIFIER(__exit__);
_Py_IDENTIFIER(__enter__);
PyObject *mgr = TOP();
PyObject *exit = special_lookup(mgr, &PyId___exit__), *enter;
PyObject *res;
```

Now, a look at the `_Py_IDENTIFIER` macro:

```
/** From: Include/object.h **/

/********************* String Literals ****************************************/
/* This structure helps managing static strings. The basic usage goes like this:
   Instead of doing

       r = PyObject_CallMethod(o, "foo", "args", ...);

   do

       _Py_IDENTIFIER(foo);
       ...
       r = _PyObject_CallMethodId(o, &PyId_foo, "args", ...);

   PyId_foo is a static variable, either on block level or file level. On first
   usage, the string "foo" is interned, and the structures are linked. On interpreter
   shutdown, all strings are released (through _PyUnicode_ClearStaticStrings).

   Alternatively, _Py_static_string allows to choose the variable name.
   _PyUnicode_FromId returns a borrowed reference to the interned string.
   _PyObject_{Get,Set,Has}AttrId are __getattr__ versions using _Py_Identifier*.
*/
typedef struct _Py_Identifier {
    struct _Py_Identifier *next;
    const char* string;
    PyObject *object;
} _Py_Identifier;

#define _Py_static_string_init(value) { 0, value, 0 }
#define _Py_static_string(varname, value)  static _Py_Identifier varname = _Py_static_string_init(value)
#define _Py_IDENTIFIER(varname) _Py_static_string(PyId_##varname, #varname)
```

Well, at least the documentation is explicit! With a little more research we can find the `dict` function we were looking for: `_PyDict_GetItemId`.

So the lookup part of our opcode will look like:

```
 /** Our callback function will be named op_target **/
PyObject *target = NULL;
_Py_IDENTIFIER(op_target);
target = _PyDict_GetItemId(f->f_globals, &PyId_op_target);
if (target == NULL && _PyErr_OCCURRED()) {
    if (!PyErr_ExceptionMatches(PyExc_KeyError))
        goto error;
    PyErr_Clear();
    DISPATCH();
}
```

To be completely explicit, this code needs a few explanations:

- `f` is our current frame and `f->f_globals` is its globals
- If we don't find `op_target`, we check if the exception is a `KeyError`
- `goto error;` is the main-loop's way of raising the exception
- `PyErr_Clear()` suppresses the current exception and `DISPATCH()` launches the evaluation of the next opcode

The next step is to gather the information we want (the stack):

```
 /** This code create a list with all the values on the current stack **/
PyObject *value = PyList_New(0);
for (i = 1 ; i <= STACK_LEVEL(); i++) {
    tmp = PEEK(i);
    if (tmp == NULL) {
        tmp = Py_None;
    }
    PyList_Append(value, tmp);
}
```

The last step is actually calling our callback! For that, we will use `call_function` and learn how to use it by looking at the opcode `CALL_FUNCTION`:

```
/** From: Python/ceval.c **/
TARGET(CALL_FUNCTION) {
    PyObject **sp, *res;
    /** stack_pointer is a local of the main loop.
        It's the pointer to the stacktop of our frame **/
    sp = stack_pointer;
    res = call_function(&sp, oparg);
    /** call_function handles the args it consummed on the stack for us **/
    stack_pointer = sp;
    PUSH(res);
    /** Standard exception handling **/
    if (res == NULL)
        goto error;
    DISPATCH();
}
```

With all that information, we are able to craft our `DEBUG_OP`:

```
TARGET(DEBUG_OP) {
    PyObject *value = NULL;
    PyObject *target = NULL;
    PyObject *res = NULL;
    PyObject **sp = NULL;
    PyObject *tmp;
    int i;
    _Py_IDENTIFIER(op_target);

    target = _PyDict_GetItemId(f->f_globals, &PyId_op_target);
    if (target == NULL && _PyErr_OCCURRED()) {
        if (!PyErr_ExceptionMatches(PyExc_KeyError))
            goto error;
        PyErr_Clear();
        DISPATCH();
    }
    value = PyList_New(0);
    Py_INCREF(target);
    for (i = 1 ; i <= STACK_LEVEL(); i++) {
        tmp = PEEK(i);
        if (tmp == NULL)
            tmp = Py_None;
        PyList_Append(value, tmp);
    }

    PUSH(target);
    PUSH(value);
    Py_INCREF(f);
    PUSH(f);
    sp = stack_pointer;
    res = call_function(&sp, 2);
    stack_pointer = sp;
    if (res == NULL)
        goto error;
    Py_DECREF(res);
    DISPATCH();
}
```

As I didn’t had that much experience with the C code in CPython, I might have missed something (I am looking at you refcounting). Feel free to correct me in this case. ;)

It compiles! So it works!

Well not really... It might seem good but this code will fail when we will try to execute our first `DEBUG_OP`. Since 2008, Python use computed goto (you can read more about computed goto in Python here). So we need to update the goto jump table: we just need to go into `Python/opcode_targets.h` and do the following change:

```
/** From: Python/opcode_targets.h **/
/** Easy change since DEBUG_OP is the opcode number 1 **/
static void *opcode_targets[256] = {
    //&&_unknown_opcode,
    &&TARGET_DEBUG_OP,
    &&TARGET_POP_TOP,
    /** ... **/
```

And that's all! We now have a fully working new opcode. The only problem is that our opcode is never called as it is inexistent in the compiled bytecode. Now we need to inject `DEBUG_OP` in the bytecode of some functions.

## Injecting opcode `DEBUG_OP` into Python bytecode

There are many ways to insert a new opcode into the Python bytecode:

- We can use the peephole optimizer just like Quarkslab did
- We can do some changes in the bytecode generation code
- We can (and we will) just modify the bytecode of some functions at runtime!

Yep, coding that new opcode was enough C for today, let's get back to the source of `Understanding Python`: some hacky, strange (somewhat magical) Python!

So, what we are going to do is:

- Take the code object of the function we want to trace
- Rewrite the bytecode to inject some `DEBUG_OP`
- Put the new code object in place

### Reminder about code object

If you have never heard of `code object`, there was a little introduction somewhere in my first article. There are also some good documentation on the net and the doc page as always (Ctrl+F "code objects").

One thing to note in the context of this article is that _code objects are not mutable_:

```
Python 3.4.2 (default, Oct  8 2014, 10:45:20)
[GCC 4.9.1] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> x = lambda y : 2
>>> x.__code__
<code object <lambda> at 0x7f481fd88390, file "<stdin>", line 1>
>>> x.__code__.co_name
'<lambda>'
>>> x.__code__.co_name = 'truc'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: readonly attribute
>>> x.__code__.co_consts = ('truc',)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: readonly attribute
```

But don't worry, we will find a way to get around.

### Our tools

To do these bytecode modifications we are going to need few tools:

- The `dis` module, used to disassemble and analyse bytecode
- `dis.Bytecode`, a new feature from `Python3.4` that is super useful for disassembly and bytecode analysis!
- A way to easily modify code object

`dis.Bytecode` disassembles a code object and give us useful information about the opcode, argument and context:

```
::python
# Python3.4
>>> import dis
>>> f = lambda x: x + 3
>>> for i in dis.Bytecode(f.__code__): print (i)
...
Instruction(opname='LOAD_FAST', opcode=124, arg=0, argval='x', argrepr='x', offset=0, starts_line=1, is_jump_target=False)
Instruction(opname='LOAD_CONST', opcode=100, arg=1, argval=3, argrepr='3', offset=3, starts_line=None, is_jump_target=False)
Instruction(opname='BINARY_ADD', opcode=23, arg=None, argval=None, argrepr='', offset=6, starts_line=None, is_jump_target=False)
Instruction(opname='RETURN_VALUE', opcode=83, arg=None, argval=None, argrepr='', offset=7, starts_line=None, is_jump_target=False)
```

To be able to modify code objects, I just created a small class that clones a code object, allows to modify the values we want and generates a new code object.

```
class MutableCodeObject(object):
    args_name = ("co_argcount", "co_kwonlyargcount", "co_nlocals", "co_stacksize", "co_flags", "co_code",
                  "co_consts", "co_names", "co_varnames", "co_filename", "co_name", "co_firstlineno",
                   "co_lnotab", "co_freevars", "co_cellvars")

    def __init__(self, initial_code):
        self.initial_code = initial_code
        for attr_name in self.args_name:
            attr = getattr(self.initial_code, attr_name)
            if isinstance(attr, tuple):
                attr = list(attr)
            setattr(self, attr_name, attr)

    def get_code(self):
        args = []
        for attr_name in self.args_name:
            attr = getattr(self, attr_name)
            if isinstance(attr, list):
                attr = tuple(attr)
            args.append(attr)
        return self.initial_code.__class__(*args)
```

Easy to use, that's one problem solved!

```
>>> x = lambda y : 2
>>> m = MutableCodeObject(x.__code__)
>>> m
<new_code.MutableCodeObject object at 0x7f3f0ea546a0>
>>> m.co_consts
[None, 2]
>>> m.co_consts[1] = '3'
>>> m.co_name = 'truc'
>>> m.get_code()
<code object truc at 0x7f3f0ea2bc90, file "<stdin>", line 1>
```

### Testing our new opcode

Now that we have the basic tools to inject some `DEBUG_OP`, we should be able to verify if our implementation is usable.

For that, we are just going to add our opcode in the simplest function ever.

```
from new_code import MutableCodeObject

def op_target(*args):
    print("WOOT")
    print("op_target called with args <{0}>".format(args))

def nop():
    pass

new_nop_code = MutableCodeObject(nop.__code__)
new_nop_code.co_code = b"x00" + new_nop_code.co_code[0:3] + b"x00" + new_nop_code.co_code[-1:]
new_nop_code.co_stacksize += 3

nop.__code__ = new_nop_code.get_code()

import dis
dis.dis(nop)
nop()

# Don't forget that ./python is our custom Python implementing DEBUG_OP
hakril@computer ~/python/CPython3.5 % ./python proof.py
  8           0 <0>
              1 LOAD_CONST               0 (None)
              4 <0>
              5 RETURN_VALUE
WOOT
op_target called with args <([], <frame object at 0x7fde9eaebdb0>)>
WOOT
op_target called with args <([None], <frame object at 0x7fde9eaebdb0>)>
```

Sounds like it works! One line might need some explanations: `new_nop_code.co_stacksize += 3`:

- `co_stacksize` represents the stack size needed by the code object
- Our `DEBUG_OP` push 3 values to the stack, so we need to reserve space for it

Now we need to be able to inject our opcode in every Python functions! Be brave!

### Rewriting bytecode

As we have seen in the last example, rewriting Python bytecode sounds easy! To inject our `DEBUG_OP` between every opcode, all we have to do is to get the offset of every opcode (injecting our opcode into arguments would be harmful) and inject our opcode at these offsets. The offsets will be easy to get, using `dis.Bytecode`.

Something like that:

```
def add_debug_op_everywhere(code_obj):
    # We get every instruction offset in the code object
    offsets = [instr.offset for instr in dis.Bytecode(code_obj)]
    # And insert a DEBUG_OP at every offset
    return insert_op_debug_list(code_obj, offsets)

def insert_op_debug_list(code, offsets):
    # We insert the DEBUG_OP one by one
    for nb, off in enumerate(sorted(offsets)):
        # Need to ajust the offsets by the number of opcodes already inserted before
        # That's why we sort our offsets!
        code = insert_op_debug(code, off + nb)
    return code

# Last problem: what does insert_op_debug looks like?
```

One might think (based on the previous example) that our `insert_op_debug` will just add a `"x00"` at the specified offset, but there is a TRAP! Our first example of `DEBUG_OP` insertion was a simple code without any branch. To have a fully functioning `insert_op_debug`, we need to take care of such branching opcodes.

Python branches are really simple, there are two types of branches:

- Absolute branches: the branch will look like `Instruction_Pointer = argument(instruction)`
- Relative branches: the branch will look like `Instruction_Pointer += argument(instruction)`
    - Relative branches are always forward

As we want those branches to be still valid after our `DEBUG_OP` insertions, we will need to rewrite those instructions arguments. So here is the logic I used:

- For every relative branch **before** our insertion offset:
    
    - If the destination is **strictly** superior to our insertion offset, add 1 to the instruction argument
    - If it is equal, no need to add 1, it will allow us the execute our `DEBUG_OP` between the jump and its target
    - If it's less, then our `DEBUG_OP` won't change the distance between the `JUMP` and the destination
- For every absolute branch in the code object:
    
    - If the destination is **strictly** superior to our insertion offset, add 1 to the instruction argument
    - No modification if it is equal, for the same reason as the relative branches
    - If it's less, our `DEBUG_OP` insertion won't change the address of the destination

Here is the implementation:

```
# Helper
def bytecode_to_string(bytecode):
    if bytecode.arg is not None:
        return struct.pack("<Bh", bytecode.opcode, bytecode.arg)
    return struct.pack("<B", bytecode.opcode)

# Dummy class for bytecode_to_string
class DummyInstr:
    def __init__(self, opcode, arg):
        self.opcode = opcode
        self.arg = arg

def insert_op_debug(code, offset):
    opcode_jump_rel = ['FOR_ITER', 'JUMP_FORWARD', 'SETUP_LOOP', 'SETUP_WITH', 'SETUP_EXCEPT', 'SETUP_FINALLY']
    opcode_jump_abs = ['POP_JUMP_IF_TRUE', 'POP_JUMP_IF_FALSE', 'JUMP_ABSOLUTE']
    res_codestring = b""
    inserted = False
    for instr in dis.Bytecode(code):
        if instr.offset == offset:
            res_codestring += b"x00"
            inserted = True
        if instr.opname in opcode_jump_rel and not inserted: #relative jump are always forward
            if offset < instr.offset + 3 + instr.arg: # inserted beetwen jump and dest: add 1 to dest (3 for size)
                #If equal: jump on DEBUG_OP to get info before exec instr
                res_codestring += bytecode_to_string(DummyInstr(instr.opcode, instr.arg + 1))
                continue
        if instr.opname in opcode_jump_abs:
            if instr.arg > offset:
                res_codestring += bytecode_to_string(DummyInstr(instr.opcode, instr.arg + 1))
                continue
        res_codestring += bytecode_to_string(instr)
    # replace_bytecode just replaces the original code co_code
    return replace_bytecode(code, res_codestring)
```

We can look at the result:

```
::python

>>> def lol(x):
...     for i in range(10):
...         if x == i:
...             break

>>> dis.dis(lol)
101           0 SETUP_LOOP              36 (to 39)
              3 LOAD_GLOBAL              0 (range)
              6 LOAD_CONST               1 (10)
              9 CALL_FUNCTION            1 (1 positional, 0 keyword pair)
             12 GET_ITER
        >>   13 FOR_ITER                22 (to 38)
             16 STORE_FAST               1 (i)

102          19 LOAD_FAST                0 (x)
             22 LOAD_FAST                1 (i)
             25 COMPARE_OP               2 (==)
             28 POP_JUMP_IF_FALSE       13

103          31 BREAK_LOOP
             32 JUMP_ABSOLUTE           13
             35 JUMP_ABSOLUTE           13
        >>   38 POP_BLOCK
        >>   39 LOAD_CONST               0 (None)
             42 RETURN_VALUE
>>> lol.__code__ = transform_code(lol.__code__, add_debug_op_everywhere, add_stacksize=3)

>>> dis.dis(lol)
101           0 <0>
              1 SETUP_LOOP              50 (to 54)
              4 <0>
              5 LOAD_GLOBAL              0 (range)
              8 <0>
              9 LOAD_CONST               1 (10)
             12 <0>
             13 CALL_FUNCTION            1 (1 positional, 0 keyword pair)
             16 <0>
             17 GET_ITER
        >>   18 <0>

102          19 FOR_ITER                30 (to 52)
             22 <0>
             23 STORE_FAST               1 (i)
             26 <0>
             27 LOAD_FAST                0 (x)
             30 <0>

103          31 LOAD_FAST                1 (i)
             34 <0>
             35 COMPARE_OP               2 (==)
             38 <0>
             39 POP_JUMP_IF_FALSE       18
             42 <0>
             43 BREAK_LOOP
             44 <0>
             45 JUMP_ABSOLUTE           18
             48 <0>
             49 JUMP_ABSOLUTE           18
        >>   52 <0>
             53 POP_BLOCK
        >>   54 <0>
             55 LOAD_CONST               0 (None)
             58 <0>
             59 RETURN_VALUE

# Setup the simplest handler EVER
>>> def op_target(stack, frame):
...     print (stack)

# GO
>>> lol(2)
[]
[]
[<class 'range'>]
[10, <class 'range'>]
[range(0, 10)]
[<range_iterator object at 0x7f1349afab80>]
[0, <range_iterator object at 0x7f1349afab80>]
[<range_iterator object at 0x7f1349afab80>]
[2, <range_iterator object at 0x7f1349afab80>]
[0, 2, <range_iterator object at 0x7f1349afab80>]
[False, <range_iterator object at 0x7f1349afab80>]
[<range_iterator object at 0x7f1349afab80>]
[1, <range_iterator object at 0x7f1349afab80>]
[<range_iterator object at 0x7f1349afab80>]
[2, <range_iterator object at 0x7f1349afab80>]
[1, 2, <range_iterator object at 0x7f1349afab80>]
[False, <range_iterator object at 0x7f1349afab80>]
[<range_iterator object at 0x7f1349afab80>]
[2, <range_iterator object at 0x7f1349afab80>]
[<range_iterator object at 0x7f1349afab80>]
[2, <range_iterator object at 0x7f1349afab80>]
[2, 2, <range_iterator object at 0x7f1349afab80>]
[True, <range_iterator object at 0x7f1349afab80>]
[<range_iterator object at 0x7f1349afab80>]
[]
[None]
```

Wonderful! We now have a way to get the state of our stack and our frame at every Python instruction. The rendering of the results is not quite usable in the current state. Let's add some wrapper in the last section!

## Adding some Python wrapping

As you can see, all of the low level interface works. Our last mission is to make our `op_target` useful. (This part might be a little empty: it's not the funniest part of this project in my eyes)

The first thing that we want to do is to exploit the information given by the frame parameter. If we look at the informations stored in a frame we can see this:

- `f_code`: the code object being executed in this frame
- `f_lasti`: gives the current instruction (this is an index into the bytecode string of the code object)

Now our handle is able to know which opcode will be executed just after our `DEBUG_OP`. This will be useful to aggregate the data and do some nice display.

We can create a class that will setup the tracing mechanism for a function:

- Change its `co_code`
- Setup a callback as the target function `op_debug`

As we know the next instruction, we can analyse it and modify its arguments. For example, we can add an `auto-follow-called-functions` feature:

```
::python

def op_target(l, f, exc=None):
    if op_target.callback is not None:
        op_target.callback(l, f, exc)

class Trace:
    def __init__(self, func):
        self.func = func

    def call(self, *args, **kwargs):
        self.add_func_to_trace(self.func)
        # Activate Trace callback for the func call
        op_target.callback = self.callback
        try:
            res = self.func(*args, **kwargs)
        except Exception as e:
            res = e
        op_target.callback = None
        return res

    def add_func_to_trace(self, f):
        # Is it code? is it already transformed?
        if not hasattr(f ,"op_debug") and hasattr(f, "__code__"):
            f.__code__ = transform_code(f.__code__, transform=add_everywhere, add_stacksize=ADD_STACK)
            f.__globals__['op_target'] = op_target
            f.op_debug = True

    def do_auto_follow(self, stack, frame):
        # Nothing fancy: FrameAnalyser is just the wrapper that gives the next executed instruction
        next_instr = FrameAnalyser(frame).next_instr()
        if "CALL" in next_instr.opname:
            arg = next_instr.arg
            f_index = (arg & 0xff) + (2 * (arg >> 8))
            called_func = stack[f_index]

            # If call target is not traced yet: do it
            if not hasattr(called_func, "op_debug"):
                self.add_func_to_trace(called_func)
```

Now, all we have to do is to implement sub-classes with the method `callback` which will be called every instruction and the method `do_report` that will print the gathered information.

Here is an example of a dummy tracer that follows function calls:

```
::python
class DummyTrace(Trace):
    def __init__(self, func):
        self.func = func
        self.data = collections.OrderedDict()
        self.last_frame = None
        self.known_frame = []
        self.report = []

    def callback(self, stack, frame, exc):
        if frame not in self.known_frame:
            self.known_frame.append(frame)
            self.report.append(" === Entering New Frame {0} ({1}) ===".format(frame.f_code.co_name, id(frame)))
            self.last_frame = frame
        if frame != self.last_frame:
            self.report.append(" === Returning to Frame {0} {1}===".format(frame.f_code.co_name, id(frame)))
            self.last_frame = frame

        self.report.append(str(stack))
        instr = FrameAnalyser(frame).next_instr()
        offset = str(instr.offset).rjust(8)
        opname = str(instr.opname).ljust(20)
        arg = str(instr.arg).ljust(10)
        self.report.append("{0}  {1} {2} {3}".format(offset, opname, arg, instr.argval))
        self.do_auto_follow(stack, frame)

    def do_report(self):
        print("n".join(self.report))
```

Here are some examples of implementation and uses. The format may be hard to read, I am not good at user-friendly reporting...

Example 1: auto-tracing with dummy dump of stack and executed instructions

Example 2: context manager at work

And, at last, a demo of how list comprehensions work:

Example 3: output of dummy tracer

Example 4: output of Stack aggregation tracer

## Conclusion

This little project was a good way to have an introduction to some low-level Python, the interpreter's main loop, Python C-coding and Python bytecode. Also, the resulting tool is a good way to have a quick look at the bytecode-behavior of some fun Python constructions like generators, context managers or list comprehensions.

Here is the complete code of this experimentation.

Another thing that could be done is adding a way to modify the stack of the function we are tracing. I am not sure what it could be used for, but that would be fun!

Go to Source
