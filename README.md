# Super-Regenerative-VHF-FM-Receiver-Radio-
My 5th Semester Electronic Circuit Design Project
Hello, Muhammad Ahmed here :)

This project is a complete Radio for the VHF Bandwidth of 85-120MHz, the Bandwidth depends on the L1 & L2 inductor + the VC1 values called an LC Tank. Credits are given to Raymond Haigh and his document "Practical Radio Circuits".

This is my first time working with Radio Frequencies and hence there are a lot of limitations and things that should've been improved:
1. Do not use simple perf boards as they have higher ground impedence. Much better to use copper clad boards due to        their lower impedence. 
2. Every connection and wire has its own inductances, capacitances. A wire is basically a transmission line at these       higher frequencies and you need to make absolutely sure that your connections are as close to each other otherwise      your capacitor at the end will be communicating with the antenna and all of the circuit.
3. Try to use PCBs than making your own solder connections.

So, why choose this design? I went with a Super-Regenerative architecture because it offers insane sensitivity (we are talking microvolts) with a very low component count. A standard radio would need way more stages to get this kind of gain. The circuit is broken down into three main stages:

The RF Buffer (Isolation):
I used a 2N2369 transistor here. This part is crucial. Since the main detector is basically an oscillator, without this buffer stage, the radio would actually transmit interference back out of the antenna and jam nearby devices. This stage acts like a "one-way valve"—letting signals in, but stopping the oscillation from getting out.

The Detector:
Heart of the project, built around a 2N3819 JFET. It uses positive feedback to build up oscillation and a "Quench" network to constantly reset itself at ultrasonic speeds (about 20kHz). This constant resetting allows it to amplify the signal nearly a million times in a single stage.

Check the T2 Oscillation Voltage image I uploaded—I measured about 0.9V at the drain, which confirms the JFET is sitting right in that sweet spot of sensitivity.

Audio Amplification: The signal coming out of the detector is tiny and mixed with high-frequency noise. I filtered that out and fed it into a separate LM386 Audio Amplifier module (which I built on a breadboard for easier testing) to drive the 8-ohm speaker.

The Tuning Struggle
As you can see in the Complete Circuit Board photos, the tuning coils (L1 & L2) are hand-wound. Since I didn't have a precise variable capacitor for the entire range, tuning involved physically stretching and squeezing the copper coil to change its inductance.

Stretching it: Lowers the inductance (Higher Frequency).

Squeezing it: Increases inductance (Lower Frequency).

It works, but it's extremely sensitive to hand capacitance—if you move your hand too close, the station drifts!

What's in this Repo?
Schematic: The full circuit diagram I followed.

Board Images: High-res shots of the main RF board (Vero board) and the separate LM386 amp.

Test Results: I've included photos of the multimeter readings (Oscillation Voltage) just to prove the hardware is actually alive and biased correctly.
