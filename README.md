FRC cRIO Serial Bridge
=========

We require a TCP to virtual COM port bridge. For this, we're going to use [com0com](http://com0com.sourceforge.net/)

This project requires WPI's FRC LabVIEW libraries installed.

1. Install the [com0com base](http://sourceforge.net/projects/com0com/files/com0com/). As of this writing, the file you want is "com0com-3.0.0.0-i386-and-x64-unsigned.zip". Follow the ReadMe. I've only tested with Windows XP, but the directions explain how to get it to work with newer Windows. In the end, you'll have two new linked COM ports. 
2. Download [com2tcp](http://sourceforge.net/projects/com0com/files/com2tcp/). No installer this time, extract com2tcp.exe to somewhere.
3. Put connect.bat in the same place. You'll have to open and modify it a bit. Change COMx to one of the new COM ports and the IP to the IP of the target.
4. Save, close, and run the batch file.
5. If enabled, disable the CAN driver on your cRIO using the FRC cRIO Imaging Tool. The driver eats serial input.
6. Run the bridge.vi on your cRIO. Don't forget to specify the IP of your robot in the project properties.
7. Congrats, you can now use the COM port on the cRIO as if it were a real serial port on your computer. Just run whatever software you want and specify the other COM port (that you didn't use in connect.bat)

Note, it's really just purely a data connection. So there's no hardware flow control, and you'll have to change bridge.vi to work with the target serial device. I initially did this for CAN stuff, so by default BDC-COMM should work. 

My brief testing has shown that the connection can be a bit slow, but it's been stable for me. BDC-COMM has successfully been able to Update Firmware and Recover Device.
