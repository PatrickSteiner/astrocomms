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

3. Add the needed [Arduino Libraries](https://www.printed-droid.com/wp-content/uploads/2020/01/SHADOW_MD_Arduino_Libraries.zip) to your local Arduino IDE, by extracting the zip file to the right location.

4. Upload the [SHADOW (MD) Sketch](https://www.printed-droid.com/wp-content/uploads/2020/01/SHADOW_MD_Sketch_.zip) to your Arduino board.

5. Use a serial monitor tool like the one provided in Arduino IDE. Select the right Board, being *Arduiono Mega or Mega 2560* and the correct Port with a baud rate of *115200*
![USB Port to configure PS3 Controller](./pictures/pic2.png)

6. Optional (but recommended): make sure that serial debugging is enabled in the source code of the USB_Host_Shield library. To do so, check for `#ENABLE_UHS_DEBUGGING 1` in settings.h, as it should be.

7. After initialization, if Debugging is enabled, the Serial Monitor should display the following:
```
PS3 Bluetooth Library Started
Bluetooth Dongle Inititialized
HCI Reset complete
Local Bluetooth Address: ##:##:##:##:##:##
Wait For Incoming Connection Request
``` 

8. Unplug the Bluetooth Dongle and connect the PS3 Move Controller via USB Cable to the USB port that previously had the Bluetooth Dongle.

9. This step will partly pair the PS3 Move Controller  to the Bluetooth Dongle, so look for the following on the Serial Monitor, with the MAC Address being the same as the one of the Dongle.
```
Navigation Controller Connected
Bluetooth Address was set to: ##:##:##:##:##:##
```

10. Disconnect the PS3 Move Controller via the USB Cable and re-insert the Bluetooth Dongle.

11. Power on the PS3 Move Controller and look for the following messages on the Serial Monitor, this time the MAC Address should be something new.
```
Gamepad is connecting
Incoming Connection Request
Remote Name: Navigation Controller
Connected to Device: ##:##:##:##:##:##
```

12. Copy the BT Address of the controller, and paste it into the sketch *Shadow_MD_DualController_Template.ino* as the MAC Address to control the Foot/Body
```
String PS3ControllerFootMac = "##:##:##:##:##:##";
```

13. Repeat steps 8 to 12 to identify the MAC Address of the second PS3 Move Controller and paste it into the variable for the MAC Address of the Dome
```
String PS3ControllerDomeMac = "##:##:##:##:##:##";
```

14. Compile and upload the altered *Shadow_MD_DualController_Template.ino* sketch to the Arduino Mega

15. When powering on both PS3 Move Controller, you should see the following messages on the Serial Monitor
```
We have our FOOT controller connected.
...
We have our DOME controller connected.
```

