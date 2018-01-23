# Adafruit NFC/RFID Shield documantation
Since Adafruit lacks documentation about how the PN532 NFC/RFID Controller Shield for Arduino works, I decided I would documentate the installation and code of the Shield. There are a lot of functions the shield has, but I will explain how the code works that can read a NFC tag. The Shield is compatible with most of the Arduino's, but I am using an Arduino Leonardo.

### Solder the shield
Before you can use the shield, you need to make sure to solder the shield. If you don't know how to solder, I recommend you to find someone to do it for you, since it's quite a precise job. Make sure every pin is only connected to the corresponding hole in the shield, and doesn't touch any other pin.
##### Note: 
If you are using the Arduino Leonardo (like I am), then you need to connect to make some adjustments to the shield. As you can see, the (2) pin is connected to the IRQ connector on the shield. This causes a problem, since the (2) is used for another task. You need to cut the connector between (2) and IRQ, and solder a wire between another pin and IRQ. The closest pin that isn't used is (6).

## The code itself
You can download the Adafruit library from here: https://github.com/adafruit/Adafruit-PN532. You need to copy-paste the examples file into your Arduino library folder to acces it from the Arduino text editor. From there, you can acces it by going to File -> Examples -> Adafruit PN523 -> ntag2xx_read. 
