---
title: "Big Chemistry: Catalysts"
date: 2025-01-29
---

![](https://hackaday.com/wp-content/uploads/2025/01/Catalyst.jpg?w=800)

I was fascinated by the idea of jet packs when I was a kid. They were sci-fi magic, and the idea that you could strap into an oversized backpack wrapped in tinfoil and fly around was very enticing. Better still was when I learned that these things weren’t powered by complicated rockets but by plain hydrogen peroxide, which violently decomposes into water and oxygen when it comes in contact with a metal like silver or platinum. Of course I ran right to the medicine cabinet to fetch a bottle of peroxide to drip on a spoon from my mother’s good silverware set. Needless to say, I was sorely disappointed by the results.

My little impromptu experiment went wrong in many ways, not least because the old bottle of peroxide I used probably had little of the reactive compound left in it. Given enough time, the decomposition of peroxide will happen all by itself. To be useful in a jet pack, this reaction has to proceed much, much faster, which was what the silver was for. The silver (or rather, a coating of samarium nitrate on the silver) acted as a catalyst that vastly increased the rate of peroxide decomposition, enough to produce jets of steam and oxygen with enough thrust to propel the wearer into the air. Using 90% pure peroxide would have helped too.

As it is for jet packs, so it is with industrial chemistry. Bulk chemical processes can rarely be left to their own devices, as some reactions proceed so slowly that they’d be commercially infeasible. Catalysts are the key to the chemistry we need to keep the world running, and reactors full of them are a major feature of many of the processes of Big Chemistry.

## Catalysis 101

The high school chemistry description of a catalyst is pretty simple: it’s a substance that helps a reaction to proceed without being consumed in the process. Take the case of the jet pack reaction, or rather a close alternative using another catalyst, manganese dioxide:

![2H_{2}O_{2} xrightarrow{small{MnO_{2}}} 2 H_{2}O + O_{2}](https://s0.wp.com/latex.php?latex=2H_%7B2%7DO_%7B2%7D+%5Cxrightarrow%7B%5Csmall%7BMnO_%7B2%7D%7D%7D+2+H_%7B2%7DO+%2B+O_%7B2%7D&bg=1a1a1a&fg=f3bf10&s=1&c=20201002)

Manganese dioxide does not appear on either the reactant side of the equation or in the products. It only facilitates the reaction, and no matter how much peroxide you pour on it, the manganese dioxide will still be there — with a few practical caveats, which we’ll discuss below. The usual explanation for how catalysts work is that they lower the activation energy of a reaction, which in turn increases the rate of the reaction. That’s fine as far as it goes, and probably enough of an explanation for the practical needs of bulk chemistry, but diving just a bit deeper into the concepts will help explain the engineering of catalysts and chemical reactors.

<iframe loading="lazy" title="Decomposition of hydrogen peroxide with Manganese dioxide" width="800" height="450" src="https://www.youtube.com/embed/S86mL5kEfBE?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Most of the catalysts used in bulk chemistry processes are heterogenous surface catalysts; heterogenous in that they are in a different physical state from the reactants, usually a solid catalyst with liquid or gaseous reactants, and surface in that the catalysis occurs at the interface between the reactant phase and the solid surface of the catalyst. Reactants can diffuse from their liquid or gaseous phase and adsorb onto the catalyst’s surface in close enough proximity to react with each other. Alternatively, reactants can migrate across the surface of the catalyst so they get close enough to react, but the key concept is that the catalyst acts something like a jig to keep the adsorbed reactants together long enough to do their thing. Once the reaction is complete, the product will release or desorb from the catalyst, freeing up the surface to be used by fresh reactants. This process — diffusion, adsorption, reaction, and desorption — is referred to as the catalytic cycle.

## Catalyst Structure

Most catalysts for bulk chemistry rely on elements from the transition metals groups, that block of elements that lives between the “towers” at either side of the periodic table. In addition to silver and manganese, metals from this block commonly used as catalysts include palladium, platinum, rhodium, rhenium, and iridium. Vanadium, used to produce sulfuric acid from sulfur dioxide, is another important transition metal catalyst, as is iron, which catalyzes ammonia synthesis in the Haber-Bosch process. The rare earth elements in this block are also used for some processes.

While it makes for a good demonstration of catalysis, the example above of dripping hydrogen peroxide onto a pile of manganese is a bit simplistic. Practical industrial catalysts are highly engineered to maximize their effectiveness while standing up to reaction conditions, which often require (or create) extreme temperatures and pressures.  Most industrial catalysts are classified as supported, which simply means that the active element or elements are applied to a non-catalytic physical structure that provides mechanical stability. Support materials run the gamut, from simple inorganic compounds like magnesium chloride to complex shapes made from silica, ceramics, or even plastics. The catalytic element can either be part of the support matrix or applied to the outer surface of the support, which is common for precious metal catalysts such as palladium or platinum.

<figure>

![](https://hackaday.com/wp-content/uploads/2025/01/Catalysts.jpg)

<figcaption>

Forbidden candies. Supported catalysts for fixed bed reactors take many forms, all optimized for packing, reactant flow, and maximum surface area. Source: Shubhrapdil, CC BY-SA 4.0, via Wikimedia Commons

</figcaption>

</figure>

The size and shape of the catalyst support is critical to its efficiency. A wide range of forms are used, with a tendency to shy away from spherical shapes as these tend to minimize surface area for a given volume. Cylindrical shapes are often used, and many catalysts have one or more holes passing through them, to increase their surface area. The size and shape of the particles also determine the flow characteristics of the catalyst, which is important in continuous chemical processes where the reactants need to pass through a catalyst. Catalytic cracking of crude oil into products like diesel, gasoline, and butane is a good example of a continuous flow catalytic process.

Even though catalysts aren’t used up in a reaction, they still wear out over time. Back in the days when it was still possible to buy leaded gasoline, it was pretty obvious when someone had mistakenly used the wrong gas in a car with a catalytic converter. The tetraethyl lead poisoned the catalysts in the exhaust system by coating the surface with lead compounds, blocking the active surface and leading to a characteristic rotten egg reek. Poisoning is just one way that catalysts become less effective over time; other common catalyst deactivation mechanisms include coking with heavy carbon deposits, fouling with unreacted compounds or contaminants, sintering of catalytic metal into large crystals rather than a smooth layer, and solid-phase transformation, where molecules from the support material migrate through the active layer and block access to it. Catalyst deactivation eventually reduces the efficiency enough that the spent catalyst has to be replaced.

## Catalyst Service With a Smile

Containing reactants and the catalyst media requires some sort of vessel. These are generically known as reactors, and while they range widely in size and features, for big chemistry processes like crude oil refining or polymer production, reactors can be among the biggest components of a plant. Reactors often take the form of a large tank or even a tower, many meters high, wrapped in pipes and equipped with catwalks and manholes and bristling with sensors and monitors. Big reactors are often very strong, able to resist high temperatures and pressures, and depending on the corrosivity and reactivity of the reactants, they may be made from materials such as stainless steel or even alloys like Monel or Inconel.

A large refinery or chemical plant may have dozens or even hundreds of reactors, all of which will require service at some point. Changing out spent catalyst is a challenging and dangerous job, so chemical operators usually outsource the job to specialist firms that do nothing but service reactors. They employ catalyst technicians who are trained for confined-space entry so they can safely get inside the reactor to inspect or clean it. Even with the proper training and safety equipment such as hazmat suits that are just this side of legitimate space suits, confined-space entry is very dangerous and can be terrifying; claustrophobiacs need not apply.

Unloading a reactor is a slow and deliberate process. Reactors tend to run very hot, so operators have to plan ahead and leave plenty of time for the reactor to cool down before unloading. Consideration also has to be given to any physical or chemical changes that occurred to the catalyst during its life, which could present a dangerous situation. Some catalysts may have accumulated metal oxides which would react violently if exposed to air, releasing deadly gasses like sulfur dioxide. In such cases, the reactor may be filled with nitrogen, which complicates technician access. Alternatively, a protective resin can be added to the reactor to coat the catalyst particles and lock away the reactive oxides, making them safer to handle.

With some reactors holding tons of catalyst, removing the spent media can be a challenge. Some reactors have dump gates at the bottom, allowing the spent material to flow out under gravity. Other reactors only have a manhole at the top, meaning that the spent catalyst has to be vacuumed out. Large, powerful vacuum trucks are used for this job, often with confined-entry techs guiding the hose inside the reactor.

The spent catalyst presents a disposal problem. In days past, spent material was either landfilled or sometimes ground up and used as a replacement for sand or gravel in concrete. This isn’t terribly sustainable, though, and when the active material of the catalyst is something like platinum, downright wasteful. Catalyst recycling is a big industry now, with companies specializing in the process. Spent catalyst is trucked off to facilities where it is classified and graded before being stripped of any remaining reactants, which are recovered and recycled where possible. Stripped catalyst is roasted in a rotary kiln to oxidize the active metal, with sulfur dioxide and particulates captured by electrostatic precipitators and filters. The roasted media, known as calcine, is ground and leached with acids to solubilize the metals, and the leachate goes through a series of pyrometallurgical processes to recover the metals.

Once a reactor has been unloaded and inspected and any necessary repairs made, it needs to be refilled with fresh catalyst. There are two main methods for this. Sock loading is where catalyst service techs enter the reactor wearing full protective suits with breath apparatus. They often need to wear special shoes to distribute their weight — think snowshoes — and prevent crushing the catalyst bed. A long flexible tube, traditionally made of canvas and hence the name of the method, is lowered to the bottom of the reactor. Catalyst particles flow down the sock from a hopper while the techs guide the sock around to make an even bed. The sock is withdrawn as the bed rises, and the techs often use rakes and shovels to evenly distribute the material.

<iframe loading="lazy" title="Calydens technology 100% catalyst Dense Loading" width="800" height="450" src="https://www.youtube.com/embed/iHyBIT_mdd0?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Another method is called dense loading. No technicians are required in the reactor; rather, a specialized dense loading tool in inserted into the tank through a central manhole at the top. The tool has a series of platforms that spin, distributing catalyst particles that are fed into the center of the tool from a hopper above. The gentle rain of catalyst particles free-falls in the reactor until it reaches the rising bed, where the particles bounce around until they settle into their lowest energy state. As the name suggests, dense loading yields a denser, more homogeneous catalyst bed, which allows more material to be packed into the same volume. This tends to make the reactor more efficient overall and increases catalyst life by decreasing hot spots.

Go to Source
