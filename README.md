# Arduino-ESP32-SDK

This repository hosts specially recompiled libraries for the [arduino-esp32](https://github.com/espressif/arduino-esp32) SDK. These libraries are compiled from the [esp-arduino-libs/esp32-arduino-lib-builder](https://github.com/esp-arduino-libs/esp32-arduino-lib-builder).

## Features

In comparison to the original arduino-esp32 SDK, this repository makes adjustments to certain sdkconfig configurations before compilation. If you need to change more configurations, you can modify the files in the *configs* folder of [esp-arduino-libs/esp32-arduino-lib-builder](https://github.com/esp-arduino-libs/esp32-arduino-lib-builder) and refer to its README for compilation details.

### For SDKs suffixed with "-d"

The SDKs in the `debug` folder change the default log level to **DEBUG** by enabling `CONFIG_LOG_DEFAULT_LEVEL_DEBUG=y` and `CONFIG_BOOTLOADER_LOG_LEVEL_INFO=y`. This increases the number of log messages printed to the serial console to aid in debugging applications.

**Important Note**: The SDKs with the "-d" suffix are only for debugging. For production purposes, please use the [official releases](https://github.com/espressif/arduino-esp32/releases) of arduino-esp32.

### For SDKs suffixed with "-h"

The SDKs in the `high_perf` folder change some configurations and can achieve higher performance in some cases, especially for avoiding [screen drifting](https://docs.espressif.com/projects/esp-faq/en/latest/software-framework/peripherals/lcd.html#why-do-i-get-drift-overall-drift-of-the-display-when-esp32-s3-is-driving-an-rgb-lcd-screen) when using RGB LCDs.

  * For ESP32-S3 SoCs:
    * All:
        * It changes the optimization level from `-Os` to `-O2` by enabling `CONFIG_COMPILER_OPTIMIZATION_PERF=y`.
        * It increases the size of the data cache line from `32` to `64` by enabling `CONFIG_ESP32S3_DATA_CACHE_LINE_64B=y`.
    * For ESP32-S3R8 (Octal PSRAM):
        * It enables the function **XIP on PSRAM** by enabling `CONFIG_SPIRAM_FETCH_INSTRUCTIONS=y` and `CONFIG_SPIRAM_RODATA=y`.

## How to Use

To use the SDKs from this repository in the Arduino IDE, follow these steps:

1. Check the version of the arduino-esp32 in use. It can be found in the Arduino IDE under `Tools > Board > Boards Manager > esp32`.
2. Ensure that the version of arduino-esp32 matches the version of the released SDKs in this repository.
3. If yes, download the released SDKs from this repository and replace the corresponding libraries in the arduino-esp32 SDK:
    * Step 1: Find the default root path of the arduino-esp32 SDK. It should be different for different operating systems:
        * For Windows, the default path is `C:\Users\<user name>\AppData\Local\Arduino15\packages\esp32`.
        * For Linux, the default path is `~/.arduino15/packages/esp32`.
    * Step 2: Find the default path of the SDK libraries. It should be different for different versions of arduino-esp32:
        * For arduino-esp32 `v2.x.x`, the default path is `hardware > esp32 > 2.x.x > tools > sdk`.
        * For arduino-esp32 `v3.x.x`, the default path is `tools > esp32-arduino-libs > idf-release_x`.
4. If not, open an issue in this repository to request a new release or refer to the [documentation](https://docs.espressif.com/projects/arduino-esp32/en/latest/lib_builder.html) for compilation instructions.