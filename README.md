# aura-cape

This is a Beaglebone cape designed to interface an ardupilot mega
(APM2) with a beaglebone linux computer.  It has been designed out of
10+ years of active UAS flight control hardware, software, and flight
test experience.  There is a fair bit of thought, experience,
different ideas tried, and lessons learned the hard way that have gone
into the design choices and development of this system.


Primary design goals:

- Maximize use of existing mature and inexpensive hardware.
- Minimize amount of custom electronic circuits, soldering, and cabling.
- Easy assembly/fabrication from kit (mostly 0.1" header soldering.)
- Minimize external wiring rats nest by pushing as many connections as
  possible onto the cape.

Features:

- Physical lay out plugs into a beaglebone as a standard cape.
- Mounting holes support a full size Ardupilot Mega 2 Atmega2560.
- Stacking layout design.
- Dual power regulation option for separate avionics and servo power
  buses.

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
