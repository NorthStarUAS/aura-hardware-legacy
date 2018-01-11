# aura-hardware

This is a repository of hardware designs that have evolved out of the
AuraUAS project.

Beaglebone cape (now with two or more variants) designed to interface
inexpensive sensors and PWM outputs to a beaglebone linux computer.
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

The existing system is designed as a beaglebone cape which interfaces
to an APM2 (atmega2560 processor).  I am also developing a new design
which compbines a teensy-3.2 and pocketbeagle on a single board.

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

- Standard cape design plugs right into a beaglebone and provides power
  and connectivity to the beaglebone.

- All versions:
  - SBUS RC Inputs
  - 8 PWM Outputs
  - Two beaglebone UARTS exposed
  - On board 5v 2.5A power regulator

- APM2 version:
  - Mounting holes to support a full size Ardupilot Mega 2 Atmega2560.
  - Stacking layout design.
  - Dual power regulation option for separate avionics and servo power
    buses.
  - Optional PWM RC Inputs

- Teensy version:
  - No extra board (no APM2 needed) to piggy back on the cape.
  - MPU-9250 IMU, BMP280 pressure sensor onboard.

Power:

- Provides clean regulated 5v power for the beaglebone and apm2 (via
  the impressive Pololu D24V22F5.)
- Exposes a 3.3v power reference (from beaglebone bus).
- Exposes the 5v avionics power bus via an RC style connector for
  future expansion.
- Optional support for an onboard 5V/5A Pololu D24V50F5 to power the
  servo bus.

Communication:

- Connects the Beaglebone to the APM2 via a UART with 3.3v <=> 5v TTL
  level translation.
- Supports a variety of 5v (3.3v TTL) radio modems such as Freescale,
  3DR, and Digi Xtend.
- Exposes the beaglebone UART4 and UART5 with DF13-5 connectors (or
  Micro-JST) to support additional components such as an external gps.

Cost:

- This cape is not currently available for sale as an assembled unit,
  but you can download the design, have it made, and populate the
  board yourself with only minimal soldering skills.  In quantities of
  3, I estimate it will cost about $60/ea to fabricate and assemble a
  full board.

The Aura Cape is designed using Express PCB, a simple, easy to learn
printed circuit board design program.  It is also the name of the
company that will fabricate the boards designed with their software.
This is not the lowest cost board fabricator but the software is
simple enough for me to learn and understand:

http://www.expresspcb.com
