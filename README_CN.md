# Arduino-ESP32-SDK

* [English Version](README.md)

这个仓库存放了专门为 [arduino-esp32](https://github.com/espressif/arduino-esp32) SDK 重新编译的库文件。这些库文件是从 [esp-arduino-libs/esp32-arduino-lib-builder](https://github.com/esp-arduino-libs/esp32-arduino-lib-builder) 编译而来的。

## 特点

与原始的 arduino-esp32 SDK 相比，本仓库在编译前对某些 sdkconfig 配置进行了调整。如果您需要更改更多配置，可以修改 [esp-arduino-libs/esp32-arduino-lib-builder](https://github.com/esp-arduino-libs/esp32-arduino-lib-builder) 中 *configs* 文件夹内的文件，并参考其 README 进行编译。

### 无后缀的 SDK

无后缀的 SDK 是默认的 SDK，它们没有任何特殊的配置更改。

* **esp32-3.1.1**（下载链接：[Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.1.1.zip)）（支持 PlatformIO）
* **esp32-3.0.7**（下载链接：[Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.0.7.zip)）（支持 PlatformIO）

### 带 "-d" 后缀的 SDK

带 "-d" 后缀的 SDK 通过启用 `CONFIG_LOG_DEFAULT_LEVEL_DEBUG=y` 和 `CONFIG_BOOTLOADER_LOG_LEVEL_INFO=y` 将默认日志级别更改为 **DEBUG**。这增加了输出到串口控制台的日志消息数量，以帮助调试应用程序。

* **esp32-2.0.13-d**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-2.0.13-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-2.0.13-d.tar.xz)）
* **esp32-3.0.0-alpha3-d**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-3.0.0-alpha3-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.0-alpha3-d.tar.xz)）
* **esp32-3.0.0-d**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-3.0.0-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.0-d.tar.xz)）
* **esp32-3.0.2-d**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-3.0.2-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.2-d.tar.xz)）
* **esp32-3.0.3-d**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/debug/esp32-3.0.3-d.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.3-d.tar.xz)）
* **esp32-3.0.7-d**（下载链接：[Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.0.7-d.zip)）（支持 PlatformIO）
* **esp32-3.1.1-d**（下载链接：[Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.1.1-d.zip)）（支持 PlatformIO）

> [!WARNING]
> 带 "-d" 后缀的 SDK 仅用于调试。对于生产用途，请使用 [无后缀的 SDK](#无后缀的-sdk)。

### 带 "-h" 后缀的 SDK

带 "-h" 后缀的 SDK 改变了一些配置，在某些情况下可以获得更高的性能，特别是在使用 RGB LCD 时可以避免[屏幕漂移](https://docs.espressif.com/projects/esp-faq/en/latest/software-framework/peripherals/lcd.html#why-do-i-get-drift-overall-drift-of-the-display-when-esp32-s3-is-driving-an-rgb-lcd-screen)。

* 对于 ESP32-S3 芯片：
  * 全部：
    * 通过启用 `CONFIG_COMPILER_OPTIMIZATION_PERF=y` 将优化级别从 `-Os` 更改为 `-O2`。
    * 通过启用 `CONFIG_ESP32S3_DATA_CACHE_LINE_64B=y` 将数据缓存线宽从 `32` 增加到 `64`。
  * 对于 ESP32-S3R8（八线 PSRAM）：
    * 通过启用 `CONFIG_SPIRAM_FETCH_INSTRUCTIONS=y` 和 `CONFIG_SPIRAM_RODATA=y` 启用 **XIP on PSRAM** 功能（< v3.1.1）。
    * 通过启用 `CONFIG_SPIRAM_XIP_FROM_PSRAM=y` 启用 **XIP on PSRAM** 功能（>= v3.1.1）。

* 对于 ESP32-P4 芯片：
  * 全部：
    * 通过启用 `CONFIG_CACHE_L2_CACHE_LINE_128B=y` 将 L2 缓存线宽从 `64` 增加到 `128`。
    * 通过启用 `CONFIG_CACHE_L2_CACHE_256KB=y` 将 L2 缓存大小从 `128KB` 增加到 `256KB`。

* **esp32-3.0.0-alpha3-h**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/high_perf/esp32-3.0.0-alpha3-h.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.0-alpha3-h.tar.xz)）
* **esp32-3.0.0-h**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/high_perf/esp32-3.0.0-h.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.0-h.tar.xz)）
* **esp32-3.0.2-h**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/high_perf/esp32-3.0.2-h.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.2-h.tar.xz)）
* **esp32-3.0.3-h**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/high_perf/esp32-3.0.3-h.tar.xz?download=) / [Espressif](https://dl.espressif.com/AE/esp-dev-kits/esp32-3.0.3-h.tar.xz)）
* **esp32-3.0.7-h**（下载链接：[Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.0.7-h.zip)）（支持 PlatformIO）
* **esp32-3.1.1-h**（下载链接：[Github](https://github.com/esp-arduino-libs/arduino-esp32-sdk/raw/master/high_perf/esp32-3.1.1-h.zip?download=) / [Espressif](https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.1.1-h.zip)）（支持 PlatformIO）

> [!WARNING]
> 对于 v3.1.1 版本的 ESP32-P4，启用 `CONFIG_COMPILER_OPTIMIZATION_PERF=y` 和 `CONFIG_SPIRAM_XIP_FROM_PSRAM=y` 会导致芯片无法正常启动。

## 如何使用

### Arduino IDE

要在 Arduino IDE 中使用本仓库的 SDK，请按照以下步骤操作：

1. 检查正在使用的 arduino-esp32 的版本。可以在 Arduino IDE 的 `工具 > 开发板 > 开发板管理器 > esp32` 中找到。
2. 确保 arduino-esp32 的版本与本仓库中发布的 SDK 版本匹配。
3. 如果匹配，从本仓库下载发布的 SDK 并替换 arduino-esp32 SDK 中对应的库：

    * **步骤 1**：找到 arduino-esp32 SDK 的默认根路径。不同操作系统的路径不同：

      * 对于 **Windows**，默认路径是 `C:\Users\<用户名>\AppData\Local\Arduino15\packages\esp32`。
      * 对于 **Linux**，默认路径是 `~/.arduino15/packages/esp32`。
      * 对于 **MacOS**，默认路径是 `~/Library/Arduino15/packages/esp32`。

    * **步骤 2**：找到 SDK 库文件的默认路径。不同版本的 arduino-esp32 路径不同：

      * 对于 arduino-esp32 `v2.x.x`，默认路径是 `hardware > esp32 > 2.x.x > tools > sdk`。
      * 对于 arduino-esp32 `v3.x.x`，默认路径是 `tools > esp32-arduino-libs > idf-release_x`。

    * **步骤 3**：SDK 库文件的结构应如下所示，用下载的 SDK 中提取的库文件替换它们：

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

4. 如果不匹配，在本仓库中提出 Issue 请求新版本发布，或参考[文档](https://docs.espressif.com/projects/arduino-esp32/en/latest/lib_builder.html)进行编译。

### PlatformIO

对于标记为 `PlatformIO Support` 的 SDK，可以直接在 PlatformIO 中使用。以 `esp32-3.1.1-h` 为例，您只需要在 `platformio.ini` 文件中添加以下内容（替换下载链接以使用其他 SDK 版本）：

```ini
platform_packages =
  platformio/framework-arduinoespressif32-libs@https://dl.espressif.com/AE/esp-arduino-libs/esp32-3.1.1-h.zip
```
