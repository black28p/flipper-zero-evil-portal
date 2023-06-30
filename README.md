# Flipper Zero Evil Portal

An evil captive portal Wi-Fi access point using the Flipper Zero and Wi-Fi dev board

## About

**This project is a work in progress.** 

This project will turn your Wi-Fi dev board into an open access point. When users try to connect to this access point they will be served a fake login screen. User credentials are sent to the Flipper and logged on the SD card.

## Disclaimer

I am not a C developer and I am using this project as a way to learn more about esp32, flipper zero and, C programming.

This program is for educational purposes only.

## Getting Started

There are pre-built .fap files for the official FW as well as unleashed FW.

You will need to manually flash the Wi-Fi dev board.

### Install pre-built app on the flipper

Go to the releases section on this repo and download and extract either the `ofw-evil_portal.zip` file or the `unleashed-evil_portal` file depending on if you are using the official firmware (ofw) or the unleashed firmware. These files will contain the `evil_portal.fap` file for your firmware.

You will also need to download and extract the `evil_portal.zip` folder. This will contain necessary files for the app to run.

Put the `evil_portal.fap` found file into the `apps/GPIO/` folder on your Flipper SD card. 

Put the `evil_portal` folder into the `apps_data` foler.
This is an example of your Flipper SD card if done correctly.

```
apps/
  GPIO/
    evil_portal.fap
apps_data/
  evil_portal/
    ap.config.txt
    index.html
    logs/
      <empty>
```
You should be able to see the `[ESP32] Evil Portal` app on your flipper zero now.

If you want to create your own `index.html` file keep in mind that there is a limit of 4000 characters for the file. I plan to increase this later but I ran into some issues with larger files.

### Install on the Wi-Fi dev board

There is no pre-built file for the Wi-Fi dev board. You will need to download the [Arduino IDE](https://www.arduino.cc/en/software) and flash the board mannually.

If you have never programmed an ESP32 using arduino before you can follow [this guide](https://lastminuteengineers.com/esp32-arduino-ide-tutorial/) to get started.

You will need to download these two libraries and move them to your Arduino library folder.

[AsyncTCP](https://github.com/me-no-dev/AsyncTCP)

[ESPAsyncWebServer](https://github.com/me-no-dev/ESPAsyncWebServer)

Go to the releases section on this repo and download the `EvilPortal.ino` file and open this in the Arduino IDE and upload this to your Wi-Fi dev board.

**Remember** you must hold down the boot button when plugging in your Wi-Fi dev board in order to flash it. 

After flashing the board and pressing the reset button you should see a solid blue light.

## Usage

Open the app on the Flipper and press `Start portal` on the main menu. After a few seconds you should start to see logs comming in from your Wi-Fi dev board and the AP will start and the LED will turn green.

The AP will take the name that is in the `ap.config.txt` file located on your Flipper in the `apps_data` folder.

When you connect to the AP a web page will open after a few seconds. This web page contains the HTML located in the `index.html` file located on your Flipper in the `apps_data` folder.

You can stop the portal by pressing `Stop portal` on the main menu. The LED should turn blue.

You can manually save logs using the `Save logs` command. Logs will be stored in the `logs` folder that is in your `apps_data/evil_portal/` folder.

Logs will automatically be saved when exiting the app or when the current log reaches 4000 characters.

## Issues

If you run into any issues make sure that you have the required files set up on the Flipper `apps_data` folder on the Flipper SD card.

If the AP won't start or you have other issues try pressing reset on the Wi-Fi dev board, waiting a few seconds, and pressing `Start portal` on the main menu.

## Todo

I plan on working on this in my free time. Here is my todo list.

* Support for multiple portals
* Enter AP name on the Flipper

## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

## Acknowledgments

I was only able to create this using the following apps as examples

* [flipperzero-wifi-marauder](https://github.com/0xchocolate/flipperzero-wifi-marauder)
* [UART_Terminal](https://github.com/cool4uma/UART_Terminal)
* [flipper-zero-fap-boilerplate](https://github.com/leedave/flipper-zero-fap-boilerplate)
* [Create Captive Portal Using ESP32](https://iotespresso.com/create-captive-portal-using-esp32/)
