# AuraUAS Autopilot Board

## Assembly Instructions and Check List

I recommend you print out these instructions on paper and actually
check off each step as it is completed.  Some steps cannot be
completed out of order!

### Tools required

- [ ] A nice solder station such as a Weller WES51.  Right now I like
  600-650F for soldering 0.1" header pins.
- [ ] A volt meter and continuity checker.
- [ ] A small clipping pliers / wire cutter.
- [ ] Needle nose pliers.
- [ ] Lighted magnifying lens (if over 40.)
- [ ] 6.5 - 36V power supply.  I have a bench power supply from Extech
  that allows me to vary the voltage and shows me the current draw,
  but a battery or simple wall wart could work fine too.

### Install Power Subsystem

- [ ] Install 3.5mm screw terminal block.
- [ ] Install TSR2-2450 voltage regulator.  Note: pin 1 on the
  TSR2-2450 has a white dot next to it.  This corresponds with the
  hole nearest the edge of the board.
- [ ] You can go ahead and power up the board at this point (I
  recommend using < 20 volt supply untile the capacitor is installed.)
  Using the schematic and board layout, test all the 5v points to make
  sure power is getting to the correct locations.
- [ ] Install the 22uf63v capacitor being careful to note polarity.
- [ ] Install the 3 x 1k ohm resistors. 
- [ ] Install the 10k ohm resistor.  Polarity does not matter with resistors.
- [ ] Go ahead and power up the board again.  Test that pin-hole A0 on
  the teensy footprint reads about 1/11 of your input voltage.  Test
  that pin-hole A1 reads about 2.5 volts.

### Install the Teensy-3.2

- [ ] Carefully scratch between the two pads on the reverse side of
  the board to disable USB power to the teensy.  This is important
  because the teensy-3.2 is not tolerant of being powered by both usb
  and onboard power simultaneiously.
  - If you forget this step before installing the teensy, there is no
    way to fix it!  But there is a work around ...
  - The recommendation is to rig up a standard USB cable with
    the red powerline snipped and still safely upload firmware to your
    teensy while it is powered by the board regulator.
  - It is just annoying because you have to remember to use the
    correct usb cable or you may significantly shorten the life of your
    teensy.
  - I recommend you clearly mark the usb port on the teensy to remind
    yourself to always use your special non-power usb cable.
- [ ] Clip rows of 0.1" header pins to fill the available holes
  between the teensy and the AuraUAS board.
- [ ] Test fit the teensy, making sure you are not shifted up or down
  by one pin.  The teensy should be centered on the footprint outline
  drawn on the board.  The teensy usb port should be at the top edge
  of the board as shown in the footprint outline.
- [ ] Carefully solder all the pins from the top side.
- [ ] Last chance!  Make sure you scratched apart the two pads on the
  bottom of the teensy.
- [ ] Flip the board over and carefully solder all the pins from the
  bottom side.
- [ ] Use your wire cutter to carefully clip all the excess length of
  the back side pins off the board.
- [ ] Power up the board.  A stock teensy should blink it's LED light
  about once per second if it is getting power properly.
- [ ] Test that you are reading 3.3 volts at the MPU-9250 breakout
  board 3.3 pin hole.
- [ ] You can install the teensy-3.2 firmware (aura-sensors) now if
  you wish or wait until later.

### Install the CJMCU MPU-9250 breakout board

- [ ] Follow the same basic technique used for the teensy.
- [ ] Clip a continuous row of 5 x 0.1" header pins (The breakout
  board may come with pins.)
- [ ] Carefully position the board (supporting the side opposite of
  the pins with a spare header pin on it's side) and solder the pins
  from the top of the board. Note that it may be a tight fit depending
  on which board you get.
- [ ] Flip the board over and solder the back side pins.  *Important:*
  be careful to ensure the breakout board is as flush as possible and
  square with the AuraUAS board. Your IMU is on this board so it the
  more accurately you place this board, the better life will be when
  it comes time to fly.
- [ ] Don't forget to clip off the excess pin material on the back
  side of the board.
- [ ] Now you can power up the board and test the firmware is able to
  read the IMU!

### Install the Pocketbeagle

- [ ] Follow the same basic procedure as the teensy and the IMU
  breakout boards.
- [ ] Clip individual and pair-wise 0.1" pins to fill in the pin-holes
  that are used by the teensy.  8 x 2-pin pairs + 1 individual pin is needed.
- [ ] Carefully position the pocketbeagle on the board.  Before
  soldering, make sure the pocketbeagle is lined up with the footprint
  lines, the usb port is facing the top side of the board, and that
  there are no missing pins.  Now go ahead and solder the pins from
  the top side.
- [ ] Flip the board over and solder the pins from the backside.  Then
  clip off the excess pin length.
- [ ] Go ahead and power the board up again.  The pocketbeagle has a
  blue led that should light up.
- [ ] If you have an SD card prepaired, you can insert it and fully
  boot up the pocketbeagle, connect to a laptop via the usb port, log
  in like it's any other beaglebone in the world, and you should be do
  all sorts of linux stuff.