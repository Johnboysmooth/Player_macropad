# Player! V1.1

Player! is a five button macropad originally designed to accomodate changing music settings in Spotify without tabbing into the Spotify client. By default it is programmed to use the built-in media keys in Windows, which can be further optimised with global hotkeys using [Toastify](https://github.com/aleab/toastify).

Using four cherry compatible switches, Player! provides dedicated keys for pausing/playing music -  returning to a previous song, and skipping to the next song. The fourth switch remains user programmable, binded to 'insert' by default to be used as dedicated Discord mute key. A rotary encoder allows for volume control, with a toggle function bound to its embedded switch to allow rotary control of rewinding and fast-forwarding music.

## License
<br />Player! is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License </a>

# Bootloader Information

The Player! uses a usb bootloader which allows the ATMega328 to program itself with QMK, namely USBaspLoader.

The custom bootloader was adapted from [coseyfannitutti](https://github.com/coseyfannitutti)'s, changing a few pin definitions, programmer choice and adding a port definiton for avrdude in my setup. 

* The bootloader is available [here](https://github.com/Johnboysmooth/USBaspLoader)
* The instructions for setting up the build environment can be found in the readme.
* Some changes may be required, such as changing the port or programmer definitions for your setup, which can be found on lines 9 and 44 of the makefile.inc respectively. **Never** edit the makefile directly.
* Flashing the ATMega328 once the build environment is setup:

	```make flash``` (flashes the makefile)

	```make fuse``` (sets fuses for ATMega328)

Assuming the flash was successful, it should now be possible to return the microcontroller to the Player! PCB and flash the [firmware] via the USB connection.

# Firmware 
Player! supports either [Vial](https://get.vial.today/) or [VIA](https://www.caniusevia.com/) for rebinding keys. It is recommended to use Vial to avoid extra steps for setting up VIA.

### Entering bootloader mode
Player! will need to be put into bootloader mode to allow QMK to be flashed via the USB connection, see below:

1. Press and hold ```Boot``` switch
2. Tap ```Reset``` switch
3. Release ```Boot``` switch

USBaspLoader will show up in device manager or as a connected device in QMK toolbox when the device has successfully entered bootloader mode, like so:
![](/Docs/Images/QMK_Toolbox.png)

## Vial Support (Easiest)

Vial compatible firmware can be flashed to the Player! using the [player_vial.hex](Firmware/player_vial.hex). 
1. In QMK_Toolbox, click "Open", then navigate to player_vial.hex and select it. 
2. Click "Flash". 
3. Following successful flash completion, press the ```Reset``` button on the PCB. 

The Player! can now be configured and is now ready to use.

## VIA Support

VIA compatible firmware can also be flashed to the Player! using the [player_via.hex](Firmware/player_via.hex), however an additional step is required.
1. In QMK_Toolbox, click "Open" then navigate to player_vial.hex and select it.
2. Click "Flash". 
3. Following successful flash completion, press the ```Reset``` button on the PCB. 
4. After opening the VIA window, navigate to the "Design" tab (which may require enabling in settings) and upload the playerkeymap.json. 

Going back to the Configure tab in VIA, the Player! can be configured and is now ready to use.

## Default Configuration

It is not required to use Vial or VIA when using the Player!, the default keymap can be flashed using the [player_default.hex](Firmware/player_default.hex). 
1. In QMK_Toolbox, click "Open" and navigate to player_default.hex and click "Flash".
2. Following successful flash completion, press the ```Reset``` button on the PCB. 

The Player! is now ready to use.

# Images
![](/Docs/Images/Player_Top.png)
![](/Docs/Images/Player_Iso.png)
![](/Docs/Images/Player_Front.png)
