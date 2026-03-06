# CAMERA WEB SERVER • ARDUINO IDE VERSION

> This repository contains multiple variants of the project.
> Switch to the appropriate Git branch to use the version you need, for example `platformio` or `arduino-ide`.

## Source

This project is based on the `CameraWebServer` example from the `esp32 by Espressif Systems` Arduino package, with local project-specific adjustments.

The original example is shipped with the ESP32 Arduino core.

On macOS, example files are typically located at:

`~/Library/Arduino15/packages/esp32/hardware/esp32/2.0.17/libraries/ESP32/examples/Camera/CameraWebServer`

## Requirements

-   Arduino IDE
-   ESP32 board package installed from:
    `https://espressif.github.io/arduino-esp32/package_esp32_index.json`
-   A compatible camera board (this repository is currently configured for `CAMERA_MODEL_XIAO_ESP32S3`)
    See: <https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html>

## Setup

-   Install Arduino IDE.
-   In Arduino IDE, open Preferences (`Cmd + ,`)
    and add this URL to **Additional Boards Manager URLs**:
    `https://espressif.github.io/arduino-esp32/package_esp32_index.json`
-   Open **Boards Manager**,
    search for `ESP32`,
    and install `esp32 by Espressif Systems` version `2.0.17` (the version used for this project).
-   Copy `WifiSettings_example.h` to `WifiSettings.h`.
-   Set your Wi-Fi credentials in `WifiSettings.h`.
-   Open `CameraWebServer.ino` and confirm the selected camera model matches your hardware.
-   Connect the board over USB,
    then select the correct board and serial port.
-   Upload the sketch.
-   Open the Serial Monitor and reset the board.
-   Wait for the message with the local URL
    (for example `http://10.97.156.39`) and open it in your browser.

## Notes

-   If you use a different ESP32 core version, behavior may differ from this repository.
-   Some camera features and resolutions require PSRAM.
-   Optional cleanup (advanced users only):
    `rm -rf ~/Library/Arduino15`
    This removes all locally installed Arduino cores/libraries from Arduino15.

## TODO

-   Investigate PSRAM requirements.
-   Confirm whether the current partition layout is appropriate.
