# pio-sparkfun_nrf52840_mini-setup

Instructions for setting up PlatformIO for [SparkFun Pro nRF52840 Mini](https://www.sparkfun.com/products/15025) development.

## Prerequisites

PlatformIO IDE is installed.

## Setup

All files needed to copy to PlatformIO directories are contained in this project's `files_to_install` directory.

1. Checkout this Git project.
2. Build the project to download the support packages for nrf52. The build is expected to fail. Run `pio run`.
3. Navigate to the PlatformIO [core_dir](https://docs.platformio.org/en/latest/projectconf/section_platformio.html#projectconf-pio-core-dir). This is `~/.platformio` on Unix and `%HOMEPATH%\.platformio` on Windows.
4. Install board file from `files_to_install`.
    * Copy `sparkfun_pro_nrf52840_mini.json` from `.\files_to_install\platforms\nordicnrf52\boards` to `.\core_dir\platforms\nordicnrf52\boards`
    * Run `pio run` again to download additional files. Thie build will fail.
5. Install variant from `files_to_install`.
    * Create directory `.\core_dir\packages\framework-arduinoadafruitnrf52\variants\sparkfun_pro_nrf52840_mini`
    * Copy `variant.h` and `variant.cpp` from `.\files_to_install\packages\framework-arduinoadafruitnrf52\variants\sparkfun_pro_nrf52840_mini` to `.\core_dir\packages\framework-arduinoadafruitnrf52\variants\sparkfun_pro_nrf52840_mini`
6. Install bootloader from `files_to_install`.
    * Create directory `.\core_dir\packages\framework-arduinoadafruitnrf52\variants\sparkfun_pro_nrf52840_mini`
    * Copy `sparkfun_pro_nrf52840_mini_bootloader-0.2.9_s140_6.1.1.hex` and `sparkfun_pro_nrf52840_mini_bootloader-0.2.9_s140_6.1.1.zip` from `.\files_to_install\packages\framework-arduinoadafruitnrf52\bootloader\sparkfun_pro_nrf52840_mini` to `.\core_dir\packages\framework-arduinoadafruitnrf52\bootloader\sparkfun_pro_nrf52840_mini`
7. Install boards.txt data.
    * Edit `.\core_dir\packages\framework-arduinoadafruitnrf52\boards.txt`
    * Copy the contents of `.\files_to_install\packages\framework-arduinoadafruitnrf52\boards_sparkfun.txt` into `boards.txt` and save it.
8. Run `pio run` again in the project directory. It should now compile successfully. You can test the program by running `pio run -t upload` and connecting to the device with [NRF Connect](https://itunes.apple.com/us/app/nrf-connect/id1054362403). See the Sparkfun guide [nRF52840 Development with Arduino and CircuitPython](https://learn.sparkfun.com/tutorials/nrf52840-development-with-arduino-and-circuitpython#arduino-examples) for more details.