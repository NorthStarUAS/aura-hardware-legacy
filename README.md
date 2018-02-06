# aura-hardware

This is a repository of hardware designs that have evolved out of the
AuraUAS project.  These designs serve the AuraUAS ecosystem -- a
completely independent small UAV autopilot system.

## bb-apm2-cape (v1.0 - v1.4)

This is the functional board design.  I have built up at least 4
functional autopilots from this design.  However, it leverages the old
APM2 (atmega2560-based) board as the sensor head.  This is functionaly
excellent, but produces a stack of 3 boards.  Also the APM2 is a very
old design now and only available through clone outlets.

## bb-teensy-cape (v1.5)

Although not listed as v1.5 in the file names, this is the logical
successor to the APM2-based board.  The APM2 is dropped and replaced
by a more modern teensy-3.2 paired with an IMU/Pressure breakout
board.  The teensy offers much more CPU power, more memory, better
ADC's, and native 3.3v ttl logic levels.

However, before this design was finished, and before I ever built a
cape, the pocketbeagle became available.  This has prompted me to move
to the next iteration.

## aura-board-expresspcb (v2.0 - 2.1)

This is a single board that combines a pocketbeagle + teensy + imu
breakout + voltage regulator + connectors in a single board package
that has only slightly larger footprint compared to the original
beaglebone.

I ordered 3x of the v2.0 board and will built up one to full flight
status.

This board was designed with the Express PCB software which also
requires ordering your boards from Express PCB.  The trade off is ease
of design versus flexibility and cost.

## aura-board-kicad (v2.2+)

The next evolution in the process is to redesign the board in kicad.
The main benefit is the ability to order the design from a multitude
of board houses, and possibly even do a pick and place shop at some
point in the future.  This gives the most flexibility and less
expensive board runs.

The next revision of the board design will shrink the footprint,
switch to screw terminals for main power input, switch to a slimmer
+5V voltage regulator, and will address a few minor issues discovered
in the v2.0/2.1 design.

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

Primary design goals:

- Maximize use of existing mature, inexpensive, and widely available
  sub-components.
- Minimize amount of custom electronic circuits, soldering, and cabling.
- Easy assembly/fabrication from kit (mostly 0.1" header soldering.)
- Minimize external wiring rats nest by pushing as many connections as
  possible onto the cape.
- High performance, high reliability, production quality flight
  results.

Features:

  - Beaglebone/Linux based flight control system (big processor).
  - Teensy/arduino based sensor interface (little processor.)
  - SBUS RC Inputs (SBUS receiver required)
  - 8 PWM Outputs (PWM servos required)
  - MPU-9250 IMU, BMP[12]80 pressure sensor.
  - 5v 2A power regulator on board.
  - Attopilot (volt/amp) sensor interface for main battery.
  - Avionics/main voltage sensing on board.
  - Beaglebone console UART exposed.
  - Supports industry standard (mRo) external devices: ublox 8 gps,
    900mhz radio modem, i2c based airspeed sensor.


Power:

- Provides clean stable 5v power for all the avionics (beaglebone,
  teensy, gps, telemetry, RC receiver, etc.)
- Servos are powered from some external source arranged by the
  integrator (for example from the ESC/throttle connector.)

Communication:

- Supports a variety of 5v (3.3v TTL) radio modems such as Freescale,
  mRo, and Digi Xtend.
- Exposes the beaglebone UART0 (console) for additional communication
  and/or debugging the beaglebone.

Cost:

- This board is not available for sale as an assembled unit.  However,
  you are welcome to download the design, have it made, and populate
  the board yourself with only minimal soldering skills.  In
  quantities of 3, I estimate it will cost about $100/ea to fabricate
  and assemble a full board.  (This doesn't include the external parts
  such as gps, radio modem, attopilot volt/amp sensor, RC system,
  etc.)

