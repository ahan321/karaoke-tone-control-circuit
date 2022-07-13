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
![](res/Block%201.png)
#### Theory of Operation
This block utilizes two important concepts pertaining to Op-Amps. The mixer mode utilizes
an inverted-summing amplifier, while the karaoke mode utilizes the subtraction amplifier.

The formula for the inverted-summing exam is as follows:

$V_{out} = -\frac{R_{1}}{R_{a}}*V_{a}-\frac{R_{2}}{R_{b}}*V_{b}$

The formula for the subtraction amplifier is as follows:

$V_{out} = -\frac{R_{2}}{R_{1}}*V_{a} + (1+\frac{R_{2}}{R_{1}})(\frac{R_{4}}{R_{3}+R_{4}})*V_{b}$

#### Derivations and Analysis
We need the output voltage of the subtraction amplifier to be -(L+R).  This can be achieved by using resistor values of 1k$\Omega$.


$V_{out} = -\frac{R_{1}}{R_{a}}*V_{a}-\frac{R_{2}}{R_{b}}*V_{b}$

$V_{out} = -\frac{1}{1}*L-\frac{1}{1}*R$

$V_{out} = -(L-R)$

Similarly, for the subtraction amplifier, we need an output of (L-R).  This can also be achieved using 1k$\Omega$ resistor values.

$V_{out} = -\frac{R_{2}}{R_{1}}*V_{a} + (1+\frac{R_{2}}{R_{1}})(\frac{R_{4}}{R_{3}+R_{4}})v$

$V_{out} = -1*V_{a} + (1+1)(\frac{1}{1+1})*V_{b}$

$V_{out} = -1*V_{a} + (2)(\frac{1}{2})*V_{b}$

$V_{out} = -1*V_{a} + (2)(\frac{1}{2})*V_{b}$

$V_{out} = -V_{a} + V_{b}$

$V_{out} = L-R$

#### Simulation Results
This capture has been generated in a simulation using values identical to the measured values in the actual experiment. This waveform exactly matches an oscilloscope capture from the actual experiment, with the SPDT switch put on both ends.

Note that the green line represents the left input, the red line represents the right input, and the orange line represents the output.

![](res/block%201%20karaoke.png)

![](res/block%201%20Mixer%20Mode.png)

### Block 2
#### Design Objective
The purpose of this block is to adjust the treble and bass frequencies of the input signal.  This feature is widely used in the music industry, and it allows for certain sound frequencies to be highlighted.  We want the gain range to be between 1/10 and 10.
#### Schematic
![](res/Block%202.png)
#### Theory of Operation
This block utilizes the baxandall-tone circuit, which has a different gain for the bass and treble components.  We need to ensure that, with a 100k$\Omega$ voltage source, the gain remains between 1/10 and 10.  The regular gain equation for a Op-Amp can be used in this case, as will be seen in the derivation.  In addition, any value of capacitors in the Baxandall-tone circuit is acceptable as long as the capacitor between the potentiometers is significantly smaller than the one on the top of the circuit.  This will ensure that the circuit works properly.
#### Derivations and Analysis
We need to start by using the maximum gain to derive the equation.  Before starting, we know that the equations for the bass and treble part of the circuit will be the same, hence the same resistors will be used in both sections.  This simplifies the calculations quite significantly.  For the maximum gain, we ensure that the potentiometer is set to 0 as it allows the top resistor ($R_{2}$) to be far larger than the bottom resistor ($R_{1}$).  The maximum gain can be found with the equation below:

$Gain = \frac{R_{2}}{R_{1}}$

We know that $R_2$ needs to be large, hence it will be 1000+R, and $R_1$ needs to be small, hence it will be just R.

$10 = \frac{100+R}{R}$

We also know that, for the smallest gain, the denominator must be far larger than the numerator.  Therefore, the potentiometer must be set 100\% of the way to the right.

$\frac{1}{10} = \frac{R}{100+R}$

When you combine the above two equations using simultaneous equations, you get that the resistance R is $11.1k\Omega$.  This is the value of all the resistors.

#### Simulation Results
This capture has been generated in a simulation using values identical to the measured values in the actual experiment. This waveform exactly matches an oscilloscope capture from the actual experiment.

The first image demonstrates the output when both potentiometers are set to 0.  The second image shows when the bass potentiometer is set to 100 while the other is 0, and the third image shows when the treble potentiometer is set to 100 with the other at 0.

Note that the blue line represents the input and the red line represents the output.

![](res/block%202%20bass%20boost.png)

![](res/block%202%20treble%20boost.png)

![](res/block%202%20flat%20response.png)
