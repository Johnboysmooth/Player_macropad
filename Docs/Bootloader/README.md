# Bootloader

The Player! uses a usb bootloader which allows the ATMega328 to program itself with QMK, namely USBaspLoader.

The custom bootloader was adapted from [coseyfannitutti](https://github.com/coseyfannitutti)'s, changing a few pin definitions, programmer choice and adding a port definiton for avrdude for my setup. 

* Player! custom bootloader is available [here](https://github.com/Johnboysmooth/USBaspLoader)
* The instructions for setting up the build environment can be found in the readme.
* Some changes may be required, such as changing the port or programmer definitions for your setup, which can be found on lines 9 and 44 of the makefile.inc respectively. **Never** edit the makefile directly.
* Flashing the ATMega328 once the build environment is setup:

	```make flash``` (flashes the makefile)

	```make fuse``` (sets fuses for ATMega328)

Assuming the flash was successful, it should now be possible to put the ATMega328 into the Player! PCB and flash the [QMK firmware](https://github.com/Johnboysmooth/qmk_firmware/tree/master/keyboards/player) via the USB connection.

#Entering bootloader mode
After flashing the microcontroller and returning it to the Player! PCB, the device will need to be put into bootloader mode to allow QMK to be flashed, see below:

1. Press and hold ```Boot``` switch
2. Tap ```Reset``` switch
3. Release ```Boot``` switch

USBaspLoader will show up in device manager or as a connected device in QMK toolbox when the device has successfully entered bootloader mode.