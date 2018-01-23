# Adafruit NFC/RFID Shield documantation
Since Adafruit lacks documentation about how the PN532 NFC/RFID Controller Shield for Arduino works, I decided I would documentate the installation and code of the Shield. There are a lot of functions the shield has, but I will explain how the code works that can read a NFC tag. The Shield is compatible with most of the Arduino's, but I am using an Arduino Leonardo.

### Solder the shield
Before you can use the shield, you need to make sure to solder the shield. If you don't know how to solder, I recommend you to find someone to do it for you, since it's quite a precise job. Make sure every pin is only connected to the corresponding hole in the shield, and doesn't touch any other pin.
#### Note: 
If you are using the Arduino Leonardo (like I am), then you need to connect to make some adjustments to the shield. As you can see, the (2) pin is connected to the IRQ connector on the shield. This causes a problem, since the (2) is used for another task. You need to cut the connector between (2) and IRQ, and solder a wire between another pin and IRQ. The closest pin that isn't used is (6). If you did this, you need to make some adjustments to the code as well. I'll come to that in a second.

## The code itself
You can download the Adafruit library from here: https://github.com/adafruit/Adafruit-PN532. You need to copy-paste the examples file into your Arduino library folder to acces it from the Arduino text editor. From there, you can acces it by going to File -> Examples -> Adafruit PN523 -> ntag2xx_read. 

#### Defining the pins
When you first open the file, you will see something like this:
```#define PN532_SCK  (2)
#define PN532_MOSI (3)
#define PN532_SS   (4)
#define PN532_MISO (5)

#define PN532_IRQ   (2)
#define PN532_RESET (3)
```
As you can see, the library itself defines two functions to the same pin. If you cut the connector between (2) and IRQ like I said at the note, you need to fill in the pin you soldered the IRQ with. When you did that, it should look something like this:
```#define PN532_IRQ   (6)
```

When you use a software or a hardware SPI connection (don't know what it is? Me neither. Luckely you will soon find out which one you're using) you need to change something in the code. 
You will find this line of code:
```Adafruit_PN532 nfc(PN532_SCK, PN532_MISO, PN532_MOSI, PN532_SS);
```
If you upload the code to your Arduino, and it works, you do not need to change anything. If it doesn't, then you need to commend the previous line out, and uncomment the following line of code:
``` Adafruit_PN532 nfc(PN532_SS);
```
There is a third option. If you use an I2C connection (don't know what this is either) then you need to commend out both lines, and uncomment this one:
``` Adafruit_PN532 nfc(PN532_IRQ, PN532_RESET);
```
Again, if you don't know which one to use, just try and see if it works.
