# CAMERA WEB SERVER • PLATFORMIO VERSION

> This repository contains multiple variants of the project.
> Switch to the appropriate Git branch to use the version you need, for example `platformio` or `arduino-ide`.

This project is based on the `CameraWebServer` example from the `esp32 by Espressif Systems` Arduino package, with local project-specific adjustments.

## Source

This project is based on the `CameraWebServer` example from the `esp32 by Espressif Systems` Arduino package, with local project-specific adjustments.

The original example is shipped with the ESP32 Arduino core.

On macOS, example files are typically located at:

`~/Library/Arduino15/packages/esp32/hardware/esp32/2.0.17/libraries/ESP32/examples/Camera/CameraWebServer`

## Requirements

-   PlatformIO with the `pio` CLI installed
-   ESP32 board package installed from:
   `https://espressif.github.io/arduino-esp32/package_esp32_index.json`
-   A compatible camera board.
    Note that this repository is currently configured for `CAMERA_MODEL_XIAO_ESP32S3` and the XIAO ESP32S3 camera pin mapping.
    See: <https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html>

## PlatformIO Setup

-   Copy `user_settings-example.ini` to `user_settings.ini`.
-   Set `upload_port` in `user_settings.ini` for your board.
-   Copy `src/WifiSettings_example.h` to `src/WifiSettings.h`.
-   Edit `src/WifiSettings.h` and set `ssid` and `password`.
-   Build and upload the `seeed_xiao_esp32s3` environment:
   `pio run -e seeed_xiao_esp32s3 -t upload`
-   Open the serial monitor if needed:
   `pio device monitor --baud 115200`

## Notes

-   `platformio.ini` and `user_settings.ini` are PlatformIO-specific for this branch.
-   Wi-Fi credentials are read from `src/WifiSettings.h`.
    This file is intended to remain a local user configuration file.
-   If you use a different ESP32 core version, behavior may differ from this repository.
-   The default high-resolution configuration expects PSRAM.
    Without PSRAM, the sketch falls back to a lower frame size.
-   Optional cleanup (advanced users only):
    `rm -rf ~/Library/Arduino15`
    This removes all locally installed Arduino cores/libraries from Arduino15.

## Usefull commands

```bash
# The ESP32S3 is blocked very often.
alias esptool.py='python3 $HOME/.platformio/packages/tool-esptoolpy/esptool.py'
PORT=/dev/cu.usbmodem20114201
esptool.py --chip esp32s3 --port $PORT erase_flash
```

## Other solutions

-   PRUSA 3D
    -   [Prusa-Firmware-ESP32-Cam — Binaries](https://github.com/prusa3d/Prusa-Firmware-ESP32-Cam/releases)
    -   [Prusa-Firmware-ESP32-Cam — Arduino IDE](https://github.com/prusa3d/Prusa-Firmware-ESP32-Cam)

## Links

-   [Préparation d’Arduino pour l’atelier IA avec la camera XIAO ESP32S3 Sense]

[Préparation d’Arduino pour l’atelier IA avec la camera XIAO ESP32S3 Sense]: https://microclub.ch/2025/04/05/preparation-darduino-pour-latelier-ia-avec-la-camera-xiao-esp32s3-sense/#comment-1358

## TODO

-   Investigate PSRAM requirements.
-   Confirm whether the current partition layout is appropriate.
