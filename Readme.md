# Astrocomms
This is my personal documentation on using, connecting and customizing [Astrocomms](https://www.printed-droid.com/kb/astrocomms/) from [Printed-Droids](https://www.printed-droid.com/).

This document is rather unstructured at this point in time. You will have to look at the various headlines to see me learnings. Once everything is up-and running and I feel that I learned all that is needed, I will restructure this document to be guideline from **Unpacking** to **playing**.


## Used Hardware
* [Astrocomms Ultra Plus with Sound out](https://shop.printed-droid.com/produkt/astrocomms-ultra-plus-with-sound-out/) with ESP32 for WLAN as the brain of my R2D2
* tbc

## Providing Power
### Power at the beginning
For the first steps, like connecting PS3 Move Controller to the Astrocomms, it is sufficient to connect any of the on-board Arduions via their USB-Ports. It obviously makes sense to connect to the one that you want to configure.

### Final Power setup
lorem ipsum

## Connect PS3 Move Controller
There is an official [documentation](https://www.printed-droid.com/kb/pairing-ps-move-controllers/) and a [YouTube video](https://www.youtube.com/watch?v=IC9cXuCXJSE) available on how to connect a PS3 Move Controller to your Astrocomms board. Unfortuntely I have found some minor glitches in those sources.

### Updated Instruction
1. Connect the USB Bluetooth Dongle to the USB Host Shield

2. Connect the Astrocomms to your computer, via the Micro-USB port of the Arduino Mega 2560 with the USB Shield. 
![USB Port to configure PS3 Controller](./pictures/pic1.png)

3. Use a serial monitor tool like the one provided in Arduino IDE. Select the right Board, being *Arduiono Mega or Mega 2560* and the correct Port
![board in Arduino IDE](./pictures/pic2.png)
Make sure you have the correct baud-rate of *115200* selected
![board in Arduino IDE](./pictures/pic3.png)



3. Optional (but recommended): Enable serial debugging. Change ENABLE_UHS_DEBUGGING to 1 in settings.h



