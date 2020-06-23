# Zvonek
A simple circuit for ringing a doorbell by briefly pressing a light switch.

The PCB was designed in EAGLE. It was milled out using a CNC. Because I needed
the PCB to be as small as possible, I had to place some of the components
outside the 1.27mm grid.

A fuse (not shown in the schematic) should be placed in series with the 12V
power line.


## Operation
The circuit is connected to a regular light switch, so that the neon lamp is
lit when the light is lit. The neon lamp is pointed at a LDR, thus forming
an optocoupler. A piece of heatshrink tubing is put over this assembly to
isolate it from ambient light.

The circuit is powered from the 12V DC bell power supply and is isolated from
the mains.

When the light is lit, a timer (about 2 s) starts. If the timer has not
finished yet and the light is already switched off, a MOSFET turns on and
the bell sounds.

```
       1   +-----------+           +---+
switch     |           |           |   |
       0 --+           +-----------+   +-------

       1   +------+                +------+
timer      |      |                |      |
       0 --+      +----------------+      +----

       1                               +---+
bell                                   |   |
       0 ------------------------------+   +---
```

This circuit should not be used with regular light bulbs, because the brief
switch-ons would reduce their lifespan. An LED light should be used instead.
