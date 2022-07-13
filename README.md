# Tone Control/Karaoke Circuit
## Introduction
I created a tone-control/karaoke-circuit using several techniques and circuit elements which
was covered this semester. This device is often used by DJ’s in order to adjust the bass and
treble of music, and is used in higher-end speaker systems as well. The project utilizes 5
different blocks, each with their own purpose. The first block combines the two channels of
sound into one sound. The second block utilizes the Baxandall tone circuit in order to allow
for adjustments to the bass and treble frequencies of the sound. The third block allows for
volume control. The fourth block has the LED’s that shows the volume level. The last block
amplifies the sound to an acceptable level in order for the output to be of an appropriate
volume.
## Design and Simulation
### Block 1
#### Design Objective
This block accepts two inputs and routes them into an OpAmp. This block consists of
two different modes, controlled by an SPDT switch. The mixer mode is achieved with an
inverted-summing amplifier, while the kareoke mode is achieved using a subtracting amplifier.
1% tolerance resistors were used in this block as this block requires a very precise resistance.
The inputs to this block is from a 3.5mm audio jack, which consists of the left, right, and
ground channel. This block outputs to the second block.
#### Schematic

