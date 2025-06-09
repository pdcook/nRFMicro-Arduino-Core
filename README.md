# Arduino Core for nRFMicro-like Boards

This repository contains the Arduino BSP for nRFMicro-compatible boards:

- [nRFMicro (DIY or ~$30 Puchi-BLE)](https://github.com/joric/nrfmicro/wiki)
- [**RECOMMENDED:** SuperMini nRF52840 (less than $3 on AliExpress)](https://wiki.icbbuy.com/doku.php?id=developmentboard:nrf52840)
- [nice!Nano v2 (~$25)](https://nicekeyboards.com/nice-nano)
- [And potentially the boards in the "ProMicro compatible" section here](https://github.com/joric/nrfmicro/wiki/Alternatives#pro-micro-compatible)

## Pinouts

### SuperMini nRF52840 / nice!Nano v2

![SuperMini nRF52840 and nice!Nano v2 pinout](https://raw.githubusercontent.com/pdcook/nRFMicro-Arduino-Core/main/supermini_nicenano.png)

### nRFMicro

![nRFMicro pinout](https://raw.githubusercontent.com/pdcook/nRFMicro-Arduino-Core/main/nrfmicro.png)

## BSP Installation

There are two methods that you can use to install this BSP. We highly recommend the first option unless you wish to participate in active development of this codebase via GitHub.

### Recommended: BSP via the Arduino Board Manager

 1. [Download and install the Arduino IDE](https://www.arduino.cc/en/Main/Software) (At least v1.6.12)
 2. Start the Arduino IDE
 3. Go into Preferences
 4. Add the following lines as 'Additional Board Manager URL'

   ```
    https://files.seeedstudio.com/arduino/package_seeeduino_boards_index.json
    https://raw.githubusercontent.com/pdcook/nRFMicro-Arduino-Core/main/package_nRFMicro_index.json
   ```

 5. Restart the Arduino IDE
 6. Open the Boards Manager from the Tools -> Board menu and install 'nRFMicro Boards'
 7. Once the BSP is installed, select 'nRFMicro' or 'SuperMini nRF52840' from the Tools -> Board menu, which will update your system config to use the right compiler and settings for the nRF52.

### Optional (Core Development): BSP via git

 1. Install BSP via Board Manager as above to install compiler & tools.
 2. Delete the core folder `nrf52` installed by Board Manager in Adruino15, depending on your OS. It could be
  * macOS  : `~/Library/Arduino15/packages/nRFMicro/hardware/nrf52`
  * Linux  : `~/.arduino15/packages/nRFMicro/hardware/nrf52`
  * Windows: `%APPDATA%\Local\Arduino15\packages\nRFMicro\hardware\nrf52`
 3. `cd <SKETCHBOOK>`, where `<SKETCHBOOK>` is your Arduino Sketch folder:
  * macOS  : `~/Documents/Arduino`
  * Linux  : `~/Arduino`
  * Windows: `~/Documents/Arduino`
 4. Create a folder named `hardware/nRFMicro`, if it does not exist, and change directories to it
 5. Clone this repo & its submodules:

   ```
   git clone https://github.com/pdcook/nRFMicro-Arduino-Core
   cd nRFMicro-Arduino-Core
   git submodule update --init
   ```
   
 6. Restart the Arduino IDE
 7. Once the BSP is installed, select 'nRFMicro' or 'SuperMini nRF52840' from the Tools -> Board menu, which will update your system config to use the right compiler and settings for the nRF52.

### Adafruit's nrfutil tools

[adafruit-nrfutil](https://github.com/adafruit/Adafruit_nRF52_nrfutil) (derived from Nordic [pc-nrfutil](https://github.com/NordicSemiconductor/pc-nrfutil)) is needed to upload sketch via serial port.

- For Windows and macOS, pre-built executable binaries are included in the BSP at `tools/adafruit-nrfutil/`. It should work out of the box.
- Linux user need to run follow command to install it from PyPi

```
$ pip3 install adafruit-nrfutil --user
```

## Credits

This core is based on [Adafruit_nRF52_Arduino](https://github.com/adafruit/Adafruit_nRF52_Arduino) by Adafruit, which in turn is based on [Arduino-nRF5](https://github.com/sandeepmistry/arduino-nRF5) by Sandeep Mistry, which in turn is based on the [Arduino SAMD Core](https://github.com/arduino/ArduinoCore-samd).

The following libraries are used:

- [FreeRTOS](https://www.freertos.org/) as operating system
- [LittleFS](https://github.com/ARMmbed/littlefs) for internal file system
- [nrfx](https://github.com/NordicSemiconductor/nrfx) for peripherals driver
- [TinyUSB](https://github.com/hathach/tinyusb) as usb stack
