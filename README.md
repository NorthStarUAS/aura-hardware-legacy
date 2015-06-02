# aura-cape

This is a Beaglebone cape designed to interface an ardupilot mega/mini
with a beaglebone linux computer.

Primary design goals:

- Maximizing existing (and inexpensive) well tested hardware.
- Minimize amount of custom electronic circuits.
- Easy assembly/fabrication from kit (mostly 0.1" header soldering.)
- Minimize wiring rats nest by pushing as many connections as possible onto
  the cape.

Features:

- Physical lay out plugs into a beaglebone as a standard cape.
- Mounting holes support a full size Ardupilot (Atmega2560) based
  board or one of the 3rd party "mini" variants.
- Stacking layout design.  It is even possible to stack the gps on top
  of the mini-apm for an even more compact integration.
- Connects the Beaglebone to the APM2 via a UART and provides TTL
  level translation.
- Provides power connections for beaglebone and apm2 (and servos) for
  single source 5v power.
- Exposes a 3.3v power reference for future expansion.
- Exposes the 5v power bus for future expansion.
- Exposes one beaglebone UART with DF13-6 connector for standard 3DR
  radio modem connection to the beaglebone.
- Exposes an extra beaglebone UART via a standard DF13 connector for
  future expansion.

This cape is designed using Express PCB, a simple, easy to learn
electronics design program.  It is also the name of the company that
can fabricate the boards you design in this software:

http://www.expresspcb.com
