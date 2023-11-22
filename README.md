# arduino-esp32-sdk

This repository is used to store specially recompiled libraries for the [arduino-esp32](https://github.com/espressif/arduino-esp32) SDK.  And the libraries in this repository are compiled from the [esp-arduino-libs/esp32-arduino-lib-builder](https://github.com/esp-arduino-libs/esp32-arduino-lib-builder). For more details about compilation instructions, please refer to the [documentation](https://docs.espressif.com/projects/arduino-esp32/en/latest/lib_builder.html).

## Features

In comparison to the original arduino-esp32 SDK, this repository has made adjustments to certain sdkconfig configurations during compilation. If need to change more configurations, can modify the files in folder *configs* of [esp-arduino-libs/esp32-arduino-lib-builder](https://github.com/esp-arduino-libs/esp32-arduino-lib-builder) and refer to its README to compile.

### For releases suffixed with "-d"

The SDK changes the default log level to **DEBUG** by enabling `CONFIG_LOG_DEFAULT_LEVEL_DEBUG=y`. This is to increase the amount of log messages printed to the serial console and help debug the application.

**Important Note**: The released SDKs suffixed with "-d" in this repository are only for debuging. For production purposes, please use the [arduino-esp32 official releases](https://github.com/espressif/arduino-esp32/releases) instead.

## Dependencies Version

| releases  | esp32-arduino-lib-builder |      esp-idf      | arduino-esp32 | esp-dl  | esp-rainmaker |   esp-camera   |  esp-littlefs  |    esp-dsp     |  tinyusb  | esp_secure_cert_mgr |
| :-------: | :-----------------------: | :---------------: | :-----------: | :-----: | :-----------: | :------------: | :------------: | :------------: | :-------: | :-----------------: |
| v2.0.13-d |       debug/v2.0.13       | v4.4.5 ac5d805d0e |   447f6db6    | 0632d24 |    b001a86    | v2.0.4 e689c3b | v1.5.5 9eeac09 | v1.4.0 8997ed9 | 39a64334a |   registry v2.2.1   |

## How to use

To use the released SDKs in this repository for Arduino IDE, please follow the below steps:

1. Check the version of the using arduino-esp32. It can be found in the Arduino IDE under `Tools > Board > Boards Manager > esp32`.
2. Check if the version of the using arduino-esp32 is the same as the version of the released SDKs in this repository.
3. If yes, directly download the released SDKs in this repository and replace the corresponding libraries in the arduino-esp32 sdk. (For windows, the default path is `C:\Users\<user name>\AppData\Local\Arduino15\packages\esp32`. For Linux, the default path is `~/.arduino15/packages/esp32`)
4. If not, please open a issue in this repository to request a new release, or refer to the [documentation](https://docs.espressif.com/projects/arduino-esp32/en/latest/lib_builder.html) to compile.
