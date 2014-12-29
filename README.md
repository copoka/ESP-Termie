ESP-Termie
==========

Modified serial terminal application and firmware tool for the ESP8266.

###Termie
Termie is a standard serial terminal application, useful when developing software on an embedded platform like the ESP8266. Printing out status messages is the most often used debugging method.
I borrowed Termmie from [Sourceforge](http://termie.sourceforge.net/), and made a few changes so that it would be better suited to developing with the ESP8266:
* I added a thread that opens and monitors a named pipe. This pipe receives requests from the firmware flashing application, esptool-py, to relinquish control of the serial port.
* I added 74880 as a baud rate choice, since that is the default speed of the chip at bootup.
* Changed some of the fonts.
* Removed the printing of <LF> for linefeeds.

###esptool-py
esptool-py is a python 2.7 program that creates and writes firmware images for the ESP8266. It is originally from [here](https://github.com/themadinventor/esptool). I just modified it so that it synchronises serial port access with the serial terminal, using the named pipe to get control when access is needed.
I also added some error handling if either the pipe or the serial port is unavailable.

