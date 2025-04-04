---
title: "It’s a weird, weird quantum world"
date: 2025-01-06
categories: 
  - "cryptography"
  - "cryptography-library"
  - "cybersecurity"
  - "cybersecurity-awareness"
  - "encryption"
  - "security"
tags: 
  - "algorithms"
  - "computerscienceandtechnology"
  - "dataprivacy"
  - "dataprotection"
  - "quantumcomputing"
---

In 1994, as Professor Peter Shor PhD ’85 tells it, internal seminars at AT&T Bell Labs were lively affairs. The audience of physicists was an active and inquisitive bunch, often pelting speakers with questions throughout their talks. Shor, who worked at Bell Labs at the time, remembers several occasions when a speaker couldn’t get past their third slide, as they attempted to address a rapid line of questioning before their time was up.

That year, when Shor took his turn to present an algorithm he had recently worked out, the physicists paid keen attention to Shor’s entire talk — and then some.

“Mine went pretty well,” he told an MIT audience yesterday.

In that 1994 seminar talk, Shor presented a proof that showed how a quantum system could be applied to solve a particular problem more quickly than a classical computer. That problem, known as the discrete logarithm problem, was known to be unsolvable by classical means. As such, discrete logarithms had been used as the basis for a handful of security systems at the time.

Shor’s work was the first to show that a quantum computer could solve a real, practical problem. His talk set the seminar abuzz, and the news spread, then became conflated. Four days after his initial talk, physicists across the country were assuming Shor had solved a related, though much thornier problem: prime factorization — the challenge of finding a very large number’s two prime factors. Though some security systems employ discrete logarithms, most encryption schemes today are based on prime factorization and the assumption that it is impossible to crack.

 “It was like the children’s game of ‘telephone,’ where the rumor spread that I had figured out factoring,” Shor says. “And in the four days since \[the talk\], I had!”

By tweaking his original problem, Shor happened to find a similar quantum solution for prime factorization. His solution, known today as Shor’s algorithm, showed how a quantum computer could factorize very large numbers. Quantum computing, once thought of as a thought experiment, suddenly had in Shor’s algorithm an instruction manual for a very real, and potentially disruptive application. His work simultaneously ignited multiple new lines of research in quantum computing, information science, and cryptography.

The rest is history, the highlights of which Shor recounted to a standing-room-only audience in MIT’s Huntington Hall, Room 10-250. Shor, who is the Morss Professor of Applied Mathematics at MIT, spoke as this year’s recipient of the James R. Killian, Jr. Faculty Achievement Award, which is the highest honor the Institute faculty can bestow upon one of its members each academic year.

In introducing Shor’s talk, Lily Tsai, chair of the faculty, quoted the award citation:

“Without exception, the faculty who nominated him all commented on his vision, genius, and technical mastery, and commended him for the brilliance of his work,” Tsai said. “Professor Shor’s work demonstrates that quantum computers have the potential to open up new avenues of human thought and endeavor.”

**A quantum history**

During the one-hour lecture, Shor took the audience through a brief history of quantum computing, peppering the talk with personal recollections of his own role. The story, he said, begins in the 1930s with the discovery of quantum mechanics — the physical behavior of matter at the smallest, subatomic scales — and the question that soon followed: Why was quantum so strange?

Physicists grappled with the new description of the physical world, which was so different from the “classical” Newtonian mechanics that had been understood for centuries. Shor says that the physicist Erwin Schrödinger attempted to “illustrate the absurdity” of the new theory with his now-famous thought experiment involving a cat in a box: How can it embody both states — dead and alive? The exercise challenged the idea of superposition, a key property of quantum mechanics that predicts a quantum bit such as an atom should hold more than one state simultaneously.

Spookier still was the prediction of entanglement, which posed that two atoms could be inextricably linked. Any change to one should then affect the other, no matter the distance separating them.

“Nobody considered using this strangeness for information storage, until Wiesner,” Shor said.

Wiesner was Stephen Wiesner, who in the late 1960s was a graduate student at Columbia University who was later credited with formulating some of the basic principles of quantum information theory. Wiesner’s key contribution was a paper that was initially spurned. He had proposed a way to create “quantum money,” or currency that was resistant to forgery, by harnessing a strange property in which quantum states cannot be perfectly duplicated — a prediction known as the “no-cloning” theorem.

As Shor remembers it, Wiesner wrote out his idea on a typewriter, sent it off for consideration by his peers, and was roundly rejected. It wasn’t until another physicist, Charles Bennett, found the paper, “pulled it out of a drawer, and got it published,” solidifying Wiesner’s role in quantum computing’s history. Bennett went further, realizing that the basic idea of quantum money could be applied to develop a scheme of quantum key distribution, in which the security of a piece of information, such as a private key passed between parties, is protected by another weird quantum property.

Bennett worked out the idea with Gilles Brassard in 1984. The BB84 algorithm was the first protocol for a crypto system that relied entirely on the weird phenomena of quantum physics. Sometime in the 1980s, Bennett came around to Bell Labs to present BB84. It was Shor’s first time hearing of quantum computing, and he was hooked.

Shor initially tried to work out an answer to a question Bennett posed to the audience: How can the protocol be proven mathematically to indeed be secure? The problem, however, was too thorny, and Shor abandoned the question, though not the subject. He followed the efforts of his colleagues in the growing field of quantum information science, eventually landing on a paper by physicist Daniel Simon, who proposed something truly weird: that a system of quantum computing bits could solve a particular problem exponentially faster than a classical computer.

The problem itself, as Simon posed it, was an esoteric one, and his paper, like Wiesner’s, was initially rejected. But Shor saw something in its structure — specifically, that the problem related to the much more concrete problems of discrete logarithms and factoring. He worked from Simon’s starting point to see whether a quantum system could solve discrete logarithms more quickly than a classical system. His first attempts were a draw. The quantum algorithm solved a problem just as fast as its classical counterpart. But there were hints that it could do better.

“There’s still hope in trying,” Shor remembers thinking.

When he did work it out, he presented his algorithm for a quantum discrete log algorithm in the 1994 symposium at Bell Labs. In the four days since his talk, he managed to also work out his eponymous prime factorization algorithm.

The reception was overwhelming but also skeptical, as physicists assumed that a practical quantum computer would instantly crumble at the barest hint of noise, resulting in a cascade of errors in its factoring computation.

“I worried about this problem,” Shor said.

So, he again went to work, looking for a way to correct errors in a quantum system without disturbing the state of the computing quantum bits. He found an answer through concatenation, which broadly refers to a series of interconnected events. In his case, Shor found a way to link qubits, and store the information of one logical, or computing qubit among nine highly entangled, physical qubits. In this way, any error in the logical qubit can be measured and fixed within the physical qubits, without having to measure (and therefore destroy) the qubit involved in the actual computation.

Shor’s new algorithm was the first quantum error correcting code that proved a quantum computer could be tolerant to faults, and therefore a very real possibility.

“The world of quantum mechanics is not the world of your intuition,” Shor said in closing his remarks. “Quantum mechanics is the way the world really is.”

**Quantum’s future**

Following his talk, Shor took several questions from the audience, including one that drives a huge effort in quantum information science today: When will we see a real, practical quantum computer?

To factor a large number, Shor estimates that a quantum system would require at least 1,000 qubits. To factor the very large numbers that underpin today’s internet and security systems would require millions of qubits.

“That’s going to take a whole bunch of years,” Shor said. “We may never make a quantum computer, ever… but if someone has a great idea, maybe we could see one 10 years from now.”

In the meantime, he noted that, as work in quantum computing has ballooned in recent years, so has work toward post-quantum cryptography and efforts to develop alternative crypto systems  that are secure against quantum-based code cracking. Shor compares these efforts to the scramble leading up to “Y2K,” and the prospect of a digital catastrophe at the turn of the last century.

“You probably should have started years ago,” Shor said. “If you wait until the last minute, when it’s clear quantum computers will be built, you will probably be too late.”

Shor received his PhD from MIT in 1985, and went on to complete a postdoc at the Mathematical Sciences Research Institute at Berkeley, California. He then spent several years at AT&T Bell Labs, and then at AT&T Shannon Labs, before returning to MIT as a tenured faculty member in 2003.

Shor’s contributions have been recognized by numerous awards, most recently with the 2023 Breakthrough Prize in Fundamental Physics, which he shared with Bennett, Brassard, and physicist David Deutsch. His other accolades include the MacArthur Fellowship, the Nevanlinna Prize (now the IMU Abacus Medal), the Dirac Medal, the King Faisal International Prize in Science, and the BBVA Foundation Frontiers of Knowledge Award. Shor is a member of the National Academy of Sciences and the American Academy of Arts and Sciences. He is also a fellow of the American Mathematical Society and the Association for Computing Machinery.
