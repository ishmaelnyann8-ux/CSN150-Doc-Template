# Cybersecurity : CSN150

## Name of Project

ESP32 Introduction: Blink

## Purpose

Set up the ESP32-CAM and Arduino environment. Upload and run the Blink sketch, then change the delay to make the LED blink faster and slower.

## Equipment

* ESP32-CAM (AI Thinker) with ESP32-CAM-MB programmer board
* USB Micro Data Cable
* MacBook (Apple Silicon)

## Links to documentation and tools

**Video 1:** CSN150 Install Arduino MAC OS (Prof. Edwin)

**Other Links:**
* Arduino IDE: https://www.arduino.cc/en/software/
* ESP32 setup guide: https://lastminuteengineers.com/esp32-arduino-ide-tutorial/
* Boards Manager URL: https://espressif.github.io/arduino-esp32/package_esp32_index.json

**AI GPTs used:** Claude

## Steps I followed

1. Installed Arduino IDE 2.3.10 for macOS.
2. Identified my board as an ESP32-CAM with the ESP32-CAM-MB board, which uses the CH340 USB chip.
3. Plugged in the board. The red power light turned on, and it showed up in Arduino IDE as `/dev/cu.usbserial-210`.
4. Added the ESP32 Boards Manager URL in Arduino IDE → Settings.
5. Installed "esp32 by Espressif Systems" (version 3.3.12) in the Boards Manager.
6. Selected "AI Thinker ESP32-CAM" as the board and `/dev/cu.usbserial-210` as the port.
7. Wrote the Blink sketch using GPIO 4 (the white flash LED).
8. Installed Rosetta through Terminal to fix a compile error (see Problems and Solutions).
9. Uploaded the sketch. The LED blinked on for 1 second and off for 1 second.
10. Changed the delay to 200 (faster) and 2000 (slower), uploading each version.

## Problems and Solutions

**Problem:** I didn't know which driver my board needed (CP210x or CH340x). **Solution:** The ESP32-CAM-MB board uses the CH340 chip, so it needs the CH340 driver.

**Problem:** I downloaded CH341SER, but it was the Windows version (.sys, .dll, SETUP.EXE files). **Solution:** I didn't need it. macOS already supports CH340, and the board appeared as `/dev/cu.usbserial-210`.

**Problem:** The board showed as "Unknown" and the search said "No boards found for ESP32-CAM". **Solution:** The ESP32 package wasn't installed. I added the Boards Manager URL and installed "esp32 by Espressif Systems".

**Problem:** Compilation error: `fork/exec .../ctags: bad CPU type in executable`. **Solution:** My Mac has an Apple Silicon chip, and this Arduino tool is built for Intel Macs. I installed Rosetta 2, which lets Apple Silicon Macs run Intel apps. I opened Terminal (Finder → Go → Utilities → Terminal) and ran:

    softwareupdate --install-rosetta --agree-to-license

It said "Install of Rosetta 2 finished successfully." I quit and reopened Arduino IDE, and the sketch compiled.

**Problem:** "Invalid sketch folder name: 'esp32 blink'". **Solution:** Sketch names can't have spaces. I renamed it `esp32_blink`.

## Final Report

The `delay()` function controls the blink speed by pausing the program in milliseconds. The first delay sets how long the LED stays on, and the second sets how long it stays off.

To make it blink **faster**, I changed both delays from 1000 to 200, so the LED blinked quickly. To make it blink **slower**, I changed both to 2000, so the light stayed on longer and went off longer.
