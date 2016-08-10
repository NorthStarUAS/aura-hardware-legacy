# aura-cape

This is a Beaglebone cape designed to interface an ardupilot mega
(APM2) with a beaglebone linux computer.

Primary design goals:

- Maximize use of existing mature and inexpensive hardware.
- Minimize amount of custom electronic circuits, soldering, and cabling.
- Easy assembly/fabrication from kit (mostly 0.1" header soldering.)
- Minimize wiring rats nest by pushing as many connections as possible onto
  the cape.

Features:

- Physical lay out plugs into a beaglebone as a standard cape.
- Mounting holes support a full size Ardupilot Mega 2 Atmega2560.
- Stacking layout design.

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

This cape is designed using Express PCB, a simple, easy to learn
electronics design program.  It is also the name of the company that
can fabricate the boards you design in this software:

http://www.expresspcb.com
