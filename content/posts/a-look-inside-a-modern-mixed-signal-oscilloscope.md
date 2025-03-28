---
title: "A Look Inside a Modern Mixed Signal Oscilloscope"
date: 2025-01-19
---

![](https://hackaday.com/wp-content/uploads/2025/01/scope-teardown-feat.jpg?w=800)

High-speed bench equipment has become so much more affordable in the last decade that naturally one wonders what has made that possible. A great source of answers is a teardown by users like \[kerry wong\] who are kind enough to take apart their MSO2304X 300MHz osilloscope for our viewing pleasure.

The posted teardown video shows the guts of the scope without enclosure, heatsinks and shields that reveal a handful of boards that execute the functions nicely. The motherboard uses the Xilinx KINTEX-7 FPGA that is expected to run core processes such as signal processing as well as managing the sample storage on the paired DDR3 memory.

The analog front-end here is a bit of a surprise as it sports TI’s ADC08D1000 ADCs that are capable of 1.3 GSPS but the scope is advertised to be capable of more. The inferred design is that all four ADCs are being operated in an interleaved symphony to achieve 5 GSPS. Testing confirms that each input uses two ADCs at a time and when two or more channels are employed, the reconstruction quality drops.

The input lanes are pretty standard and are equipped with amps and power regulators that are more than up to the task. More TI chips are discovered such as the DAC128S085 that are the key to the analog waveform generator which is a feature commonly found in modern high-end oscilloscopes. On the application processor side, the scope has a Rockchip RK3568 that is responsible for the GUI and other user-level functions.

An interesting point in the video was how lean the construction is as well as the cost. The FPGA, ADCs, and other analog components are estimated to total the sale price of the scope, which means that manufacturer pricing would have to be heavily discounted to grant gross margin on sales. We loved the review of the scope and is the other part of the story.

<iframe title="UNI-T MSO2304X Complete Teardown - Inside UNI-T's 300 Mz Mixed Signal Oscilloscope" width="800" height="450" src="https://www.youtube.com/embed/rY8mqdbomXA?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Go to Source
