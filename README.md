# AuraUAS Autopilot Hardware

This is a repository of hardware designs that have evolved out of the
AuraUAS project.  These designs serve the AuraUAS ecosystem.

## Version 1.0 - 1.4 (May 2015 - August 2016)

Beaglebone Black + Custom Cape + APM2

This is the first functional autopilot board design I created myself.
I have built up at least 4 flying autopilots from this design.
However, it leverages the old APM2 (atmega2560-based) board as the
sensor head.  This results actually are quite good, but it leads to a
stack of 3 boards and a fairly inefficient layout.  Also the APM2 is a
very old design now, has some limitations, and only available through
clone outlets.

## Version 1.5 (January 2017)

Beaglebone Black + Custom Cape + Teensy-3.2

Although not listed as v1.5 in the file names, this is the logical
successor to the APM2-based board.  The APM2 is dropped and replaced
by a more modern teensy-3.2 paired with an IMU/Pressure breakout
board.  The teensy offers much more CPU power, more memory, better
ADC's, and native 3.3v ttl logic levels.

The system was breadboarded and the overall concept proved out.
However, before this design was finished or built, the pocketbeagle
became available.  This has prompted me to move to the next iteration.

## Version 2.0 - 2.1 (January 2018)

Pocketbeagle + Teensy-3.2 + Custom Board (designed with Express PCB)

This is a single board that combines a pocketbeagle + teensy + imu
breakout + voltage regulator + connectors in a single board package
that has only slightly larger footprint compared to the original
beaglebone.

I ordered a test run of the v2.0 board and built up one to full flight
status.

This board was designed with the Express PCB software which also
requires ordering your boards from Express PCB.  The trade off is ease
of design versus flexibility and cost.

## Version 2.2 (February 2018)

Pocketbeagle + Teensy-3.2 + Custom Board (kicad + Oshpark)

The next evolution of the board is a redesign in kicad.  The main
benefit is the ability to order the design from a multitude of board
houses, and possibly even do a pick and place shop at some point in
the future.  This gives the most flexibility and less expensive board
runs.

Oshpark is a great inexpensive option.  They can suck in my kicad pcb
file directly, and they are open-source and community-sharing
friendly.

Major updates:
- Switch to the awesome kicad PCB design tool.
- Rearrange and move some parts to shrink the board footprint and
  simplify trace routing.
- Cleans up a few small goof ups in the v2.0 design.
- Switch to the TSR2-2450 power supply (functionally similar but
  slimmer and cleaner looking.)
- Add a voltage divider/sensor circuit for main input battery voltage
  (to complement the regulated voltage sensor.)
- Switch to a robust screw terminal connector for main power.


## Version 2.3 (Date: in development)

Pocketbeagle + Teensy-3.2 + Custom Board (kicad + Oshpark)

Major updates:
- Experiment with kicad's autorouting feature.
- Some component placement tweaks based on the build up of the v2.2
  board (pending.)

## Overview

These board designs support the AuraUAS autopilot flight code and
firmware.  The goal is to offer a relatively simple DIY "kit build"
solution for fixed wing UAV autopilots.  Attention is put towards
using inexpensive, but powerful off the shelf components.  Assembly is
relatively simple (mostly 0.1" header soldering.)  Overall cost is
comparable to other small UAV autopilot systems.

The basic architecture of the system employs a 'little' processor and
a 'big' processor working together as a distributed system.  The
little processor handles all the hard real time sensor I/O tasks.  The
big processor does all the heavy lifting, ekf, control, navigation,
logging, communication, and higher level logic and functions.

This system has been developed based on experience with UAS flight
control hardware, software, and flight test experience starting around
2005.  There is a fair bit of thought, experience, different ideas
tried, and lessons learned the hard way that have gone into the design
choices, development, and tuning of this system.

The following information needs to be reviewed and updated, but is
still mostly reliable.

## Primary design goals

- Maximize use of existing mature, inexpensive, and widely available
  sub-components.
- Minimize amount of custom electronic circuits, soldering, and cabling.
- Easy assembly/fabrication from kit (mostly 0.1" header soldering.)
- Minimize external wiring rats nest by pushing as many connections as
  possible onto the cape.
- High performance, high reliability, production quality flight
  results.

## Features

- Beaglebone/Linux based flight control system (big processor).
- Teensy/arduino based sensor interface (little processor.)
- SBUS RC Inputs (SBUS receiver required)
- 8 PWM Outputs (PWM servos required)
- MPU-9250 IMU, BMP[12]80 pressure sensor.
- 5v 2A power regulator on board.
- Attopilot (volt/amp) sensor interface for main battery.
- Avionics/main voltage sensing on board.
- Pocketbeagle console UART exposed.
- Supports industry standard (mRo) external devices: ublox 8 gps,
  900mhz radio modem, i2c based airspeed sensor.
- Mature firmware, autopilot flight code, and ground station interface.

## Power

- Input power can be anything that ranges from 6.5-36 volts.
- The board includes a 5V 2A regulator to provide clean stable power
  for all the avionics (pocketbeagle, teensy, gps, telemetry, RC
  receiver, etc.)
- Servos are powered from some external source arranged by the
  integrator (for example from the ESC via the throttle channel.)

## Communication

- Supports a variety of 5v (3.3v TTL) radio modems such as Freescale,
  mRo, and Digi Xtend.
- Exposes the mini-usb port on both the Teensy and the Pocketbeagle
  for updating firmware or debugging.
- Exposes the beaglebone UART0 (console) for additional communication
  and/or debugging the beaglebone.

## Cost

This board is not available for sale as an assembled unit.  However,
you are welcome to download the design, have it made, and populate the
board yourself with only minimal soldering skills.  In quantities of
3, I estimate it will cost about $100/ea to assemble a full board.

The external components such as gps, radio modem, receiver, attopilot
volt/current sensor, etc. need to be purchased separately.  These are
things that are required for any autopilot system.

