---
title: "Capacitor Decoupling Chaos, and Why You Should Abandon 100 nF"
date: 2025-01-26
---

![](https://hackaday.com/wp-content/uploads/2016/06/capacitors.jpg?w=800)

Everyone knows that the perfect capacitor to decouple the power rails around ICs is a 100 nF ceramic capacitor or equivalent, yet where does this ‘fact’ come from and is it even correct? These are the questions that \[Graham\] set out to answer once and for all. He starts with an in-depth exploration of the decoupling capacitor (and related) theory. \[Graham\] then dives into the way that power delivery is affected by the inherent resistance, capacitance, and inductance of traces. This is the problem that decoupling capacitors are supposed to solve.

Effectively, the decoupling capacitor provides a low-impedance path at high frequencies and a high-impedance path at low frequencies. Ideally, a larger value capacitor would be better, but since this is the real world and capacitors have ESL and ESR parameters, we get to look at impedance graphs. This is the part where we can see exactly what decoupling effect everyone’s favorite 100 nano-farad capacitors have, which as it turns out is pretty miserable.

Meanwhile, a 1 µF (ceramic) capacitor will have much better performance, as shown with impedance graphs for MLCC capacitors. As a rule of thumb, a single large decoupling capacitor is better, while two MLCC side-by-side can worsen noise. Naturally, one has to keep in mind that although ‘more capacity is better for decoupling’, there is still such a thing as ‘inrush current’ so don’t go too crazy with putting 1,000 µF decoupling capacitors everywhere.

Go to Source
