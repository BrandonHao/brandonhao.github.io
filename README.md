## Hi, I'm Brandon Hao

This is my website where I'll be posting my projects. I'll be including project descriptions and pictures.

### Table of Contents 
1. [Musical Tesla Coil](#Musical-Tesla-Coil)
2. [Magnetic Levitator](#Magnetic-Levitator)
3. [Chess Robot](#Chess-Robot)

### Musical Tesla Coil <a name="Musical-Tesla-Coil"></a>

This was a project I worked on for around 5 months between May and October of 2019. The goal was to design and construct a tesla coil capable of arcing to the environment while playing music. The design is a single resonant solid state tesla coil consisting of a machine wound coil and a top load made from aluminum wire wrapped around a 3D printed shell. It has a resonant frequency of around 160KHz and is capable of generating upwards of 1 million volts from a 30 volt DC supply. The music was then played by interrupting the output of the coil at the frequency of the music, this was accomplished by an op-amp with adjustable gain feeding in to a comparator with a 160KHz sawtooth wave. That output then fed into a MOSFET driver, then into 2 MOSFETs that drove the coil (2 MOSFETs in parallel to improve power dissipation).

![TC1](https://i.imgur.com/PmnCNT1.jpg)
The Tesla Coil driven off of a 30 volt supply arcing to the environment. The EMF was so intense while the coil was on that my phone touchscreen would bug out completely if it was brought anywhere close so the pictures are somewhat blurry.

![TC2](https://i.imgur.com/BC3Oqpc.jpg) 
The Tesla Coil driven at around 60 volt arcing to a screwdriver I was holding.

![assembly](https://i.imgur.com/3kMVPvn.jpg)
Stuffed PCB.

The circuit and PCB layout were designed by myself in Altium. It consists mainly of 3 parts. 

First, an op-amp oscillator generates a sawtooth wave with an adjustable frequency. This was originally designed for frequencies between 0.5 and 1.5MHz since my first 2 secondary coils had a resonance frequency of around 1.2MHz due to their low inductances. This had to change however for my final coil as it was wound much better and had a much higher inductance and therefore a much lower resonance frequency of 160KHz.
![sawtooth](https://i.imgur.com/lVXEp4F.jpg)

Second was the audio input which was amplified using an op-amp with adjustable gain and level. This was to boost the audio signal from a portable MP3 player or phone from a voltage to a range matching the sawtooth wave. This was necessary because the audio levels from a portable output are relatively low and would not be high enough to interupt the sawtooth wave. There was also an adjustable level to shift the wave up or down without changing the gain, this was to increase the drive to the circuit if I simply wanted bigger arcs without changing gain.
![audio](https://i.imgur.com/lVXEp4F.jpg)

Third and last, the audio signal was then compared to the sawtooth wave and if the audio signal was higher than the sawtooth, the output would be higher. The output was then fed into the driving circuit, which was composed of a MOSFET driver and 2 MOSFETs in parallel. Originally it was planned as 4 MOSFETs but I had broken a few by driving the circuit too hard so I had only 2 left when I finally got the final tuning and coil, it seemed to work fine so I didn't end up populating the last 2.

![power-supply](https://i.imgur.com/86xqMX5.jpg)
The power supply section of the circuit

![signal-generation](https://imgur.com/zRidB0V.png)
Overall signal generation

![MOSFETs](https://i.imgur.com/nlQZIMD.png)
MOSFETs

![Schematic](https://i.imgur.com/nG1ddvY.png)
Overall schematic - it's kind of hard to see unless you open it in a new tab.

In the process of constructing this project I wound 3 secondary coils, with the first 2 by hand. After the 2nd iteration I realized that hand-wound coils would be too imperfect for this so I put together a jig from an old fixture and a DC motor. This produced the nice coil in the final project.

![Coil-Winder](https://i.imgur.com/XCHzVIW.jpg)

## Magnetic Levitator <a name="Magnetic-Levitator"></a>
The magnetic levitator was a project with the goal of levitating a magnetic load in the air using an electromagnet. The physical design is pretty simple, consisting of an electromagnetic with a Hall Effect Sensor on an arm mounted to a box that contained all the electronics. The principle behind the levitator was to use the Hall Effect Sensor to detect the distance between the load and the electromagnet, then to turn on the coil if it was too far, or turn it off if it was too close.

![ML2](https://i.imgur.com/yU6a6Bv.jpg)
Levitation during testing

![ML1](https://i.imgur.com/0BQRLdp.jpg)
Final assembly

![PCB](https://i.imgur.com/IQi91on.png)
PCB Layout of the circuit

To accomplish this there were 3 main parts of the circuit. The first part of the circuit was the Hall Effect Sensor (HES). The HES gave a very small reading at the distance that was ideal for the magnet, so it was necessary to have a very high gain without losing too much of the resolution. Therefore, I used a multi-stage op-amp circuit to bring the levels of the sensor to the level required and used a trim part to fine tune. This signal was then fed into a comparator with the square wave.

![HES](https://i.imgur.com/IFBvauV.png)
HES and amplification

The second part used a 555 timer to create a square wave. This square wave then was buffered before before being fed into a comparator with the amplified HES readings. This was to create the oscillation required to turn on and off the coil. 
![timer](https://i.imgur.com/JGlnTNS.png)
The 555 timer circuit.

## Chess Robot <a name="Chess-Robot"></a>

I designed and created this robot as part of a team of 3. It was constructed using LEGO Mindstorm Robotics parts for the mechanical setup. The robot mechanically consists of a pick and place claw on a carriage that allowed it to access any piece on the board. The robot was controlled using an external app through Bluetooth. The app would take a picture of the board, analyse it using OpenCV, run the board-state through a home-rolled machine learning algorthim, then send the best calculated move to the NXT brick through Bluetooth which would then move the piece accordingly.

Code located here: https://github.com/David-D-White/Cheebo

![claw](https://i.imgur.com/a1LSJmj.jpg)
Image of the claw used to pick up and move pieces.

![Carriage](https://i.imgur.com/ymT2ajp.jpg)
The mechanical assembly.
