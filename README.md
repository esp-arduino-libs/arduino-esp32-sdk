# Arduino-ESP32-SDK

* [中文版本](README_CN.md)

This repository hosts specially recompiled libraries for the [arduino-esp32](https://github.com/espressif/arduino-esp32) SDK. These libraries are compiled from the [esp-arduino-libs/esp32-arduino-lib-builder](https://github.com/esp-arduino-libs/esp32-arduino-lib-builder).

## Features

In comparison to the original arduino-esp32 SDK, this repository makes adjustments to certain sdkconfig configurations before compilation. If you need to change more configurations, you can modify the files in the *configs* folder of [esp-arduino-libs/esp32-arduino-lib-builder](https://github.com/esp-arduino-libs/esp32-arduino-lib-builder) and refer to its README for compilation details.

### For SDKs without suffixes

The SDKs without suffixes are the default SDKs, they don't have any special configuration changes.

* **esp32-3.0.7** (Download Link: [Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.0.7.zip)) (PlatformIO Support)
* **esp32-3.1.1** (Download Link: [Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.1.1.zip)) (PlatformIO Support)

### For SDKs suffixed with "-d"

The SDKs suffixed with "-d" change the default log level to **DEBUG** by enabling `CONFIG_LOG_DEFAULT_LEVEL_DEBUG=y` and `CONFIG_BOOTLOADER_LOG_LEVEL_INFO=y`. This increases the number of log messages printed to the serial console to aid in debugging applications.

* **esp32-2.0.13-d** (Download Link: [Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-2.0.13-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-2.0.13-d.tar.xz))
* **esp32-3.0.0-alpha3-d** (Download Link: [Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-3.0.0-alpha3-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.0-alpha3-d.tar.xz))
* **esp32-3.0.0-d** (Download Link: [Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-3.0.0-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.0-d.tar.xz))
* **esp32-3.0.2-d** (Download Link: [Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-3.0.2-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.2-d.tar.xz))
* **esp32-3.0.3-d** (Download Link: [Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-3.0.3-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.3-d.tar.xz))
* **esp32-3.0.7-d** (Download Link: [Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.0.7-d.zip)) (PlatformIO Support)
* **esp32-3.1.1-d** (Download Link: [Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.1.1-d.zip)) (PlatformIO Support)

> [!WARNING]
> The SDKs with the "-d" suffix are only for debugging. For production purposes, please use the [SDK without suffixes](#for-sdks-without-suffixes) or [Official Releases](https://github.com/espressif/arduino-esp32/releases) of arduino-esp32.

### For SDKs suffixed with "-h"

The SDKs suffixed with "-h" change some configurations and can achieve higher performance in some cases, especially for avoiding [screen drifting](https://docs.espressif.com/projects/esp-faq/en/latest/software-framework/peripherals/lcd.html#why-do-i-get-drift-overall-drift-of-the-display-when-esp32-s3-is-driving-an-rgb-lcd-screen) when using RGB LCDs.

* For ESP32-S3 SoCs:
  * All:
    * It changes the optimization level from `-Os` to `-O2` by enabling `CONFIG_COMPILER_OPTIMIZATION_PERF=y`.
    * It increases the size of the data cache line width from `32` to `64` by enabling `CONFIG_ESP32S3_DATA_CACHE_LINE_64B=y`.
  * For ESP32-S3R8 (Octal PSRAM):
    * It enables the function **XIP on PSRAM** by enabling `CONFIG_SPIRAM_FETCH_INSTRUCTIONS=y` and `CONFIG_SPIRAM_RODATA=y` (< v3.1.1).
    * It enables the function **XIP on PSRAM** by enabling `CONFIG_SPIRAM_XIP_FROM_PSRAM=y` (>= v3.1.1).

* For ESP32-P4 SoCs:
  * All:
    * It increases the size of the L2 cache line width from `64` to `128` by enabling `CONFIG_CACHE_L2_CACHE_LINE_128B=y`.
    * It increases the size of the L2 cache line size from `128KB` to `256KB` by enabling `CONFIG_CACHE_L2_CACHE_256KB=y`.

* **esp32-3.0.0-alpha3-h** (Download Link: [Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/high_perf/esp32-3.0.0-alpha3-h.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.0-alpha3-h.tar.xz))
* **esp32-3.0.0-h** (Download Link: [Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/high_perf/esp32-3.0.0-h.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.0-h.tar.xz))
* **esp32-3.0.2-h** (Download Link: [Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/high_perf/esp32-3.0.2-h.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.2-h.tar.xz))
* **esp32-3.0.3-h** (Download Link: [Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/high_perf/esp32-3.0.3-h.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.3-h.tar.xz))
* **esp32-3.0.7-h** (Download Link: [Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.0.7-h.zip)) (PlatformIO Support)
* **esp32-3.1.1-h** (Download Link: [Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.1.1-h.zip)) (PlatformIO Support)
* **esp32-3.2.0-h** (Download Link: [Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.2.0-h.zip)) (PlatformIO Support)

> [!WARNING]
> For the ESP32-P4 in version v3.1.1 and above, enabling `CONFIG_COMPILER_OPTIMIZATION_PERF=y` and `CONFIG_SPIRAM_XIP_FROM_PSRAM=y` will cause the chip to fail to boot properly.

## How to Use

### Arduino IDE

To use the SDKs from this repository in the Arduino IDE, follow these steps:

1. Check the version of the arduino-esp32 in use. It can be found in the Arduino IDE under `Tools > Board > Boards Manager > esp32`.
2. Ensure that the version of arduino-esp32 matches the version of the released SDKs in this repository.
3. If yes, download the released SDKs from this repository and replace the corresponding libraries in the arduino-esp32 SDK:

    * **Step 1**: Find the default root path of the arduino-esp32 SDK. It should be different for different operating systems:

      * For **Windows**, the default path is `C:\Users\<user name>\AppData\Local\Arduino15\packages\esp32`.
      * For **Linux**, the default path is `~/.arduino15/packages/esp32`.
      * For **MacOS**, the default path is `~/Library/Arduino15/packages/esp32`.

    * **Step 2**: Find the default path of the SDK libraries. It should be different for different versions of arduino-esp32:

      * For arduino-esp32 `v2.x.x`, the default path is `hardware > esp32 > 2.x.x > tools > sdk`.
      * For arduino-esp32 `v3.x.x`, the default path is `tools > esp32-arduino-libs > idf-release_x`.

    * **Step 3**: The structure of the SDK libraries should be as follows, replace them with the libraries extracted from the downloaded SDK:

      ```
      idf-release_x
      ├── esp32
      ├── esp32c3
      ├── esp32c6
      ├── ...
      ├── packages.json
      ├── tools.json
      ├── versions.txt
      ```

4. If not, open an issue in this repository to request a new release or refer to the [documentation](https://docs.espressif.com/projects/arduino-esp32/en/latest/lib_builder.html) for compilation instructions.

### PlatformIO

For SDKs marked with `PlatformIO Support`, they can be used directly in PlatformIO. Taking `esp32-3.1.1-h` as an example, you just need to add the following content to the `platformio.ini` file (Replace the download link to use other SDK versions):

```ini
platform_packages =
  platformio/framework-arduinoespressif32-libs@https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.1.1-h.zip
```
