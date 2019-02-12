# Character LCD Display

## Summary
This device binding is meant to work with character LCD displays which use a HD44780 compatible controller. Almost all character LCDs fall into this category. Simple wrappers for 16x2 and 20x4 variants are included.

## Device Family
This binding has been tested with a variety of 16x2 and 20x4 displays both in 4bit and 8bit mode and via i2C adapters (such as on the CrowPi). It should work with any character LCD with a 5x8 size character. Common names are 1602LCD and 2004LCD.

## Binding Notes
These devices are controlled purely by GPIO. There are two different types of GPIO pins that are used, the control pins, and the data pins. The data pins are the ones that will send out the text that should be printed out on the LCD screen. This binding supports two different configurations for the data pins: using 4 data pins, and using 8 data pins. When using only 4 data pins, we will require two send two messages to the controller, each sending half of the byte that should be printed.

Here is a Hello World example of how to consume this binding:
```c#
using (var lcd = new Lcd1602(18, 5, new int[]{6, 16, 20, 21})) //using 4 data pins
{
    lcd.Write("Hello World!");
}
```

## References 
- Very complete tutorial on how to connect and work with one of these displays: https://learn.adafruit.com/drive-a-16x2-lcd-directly-with-a-raspberry-pi/overview
- Good guide explaining how the device works internally: http://www.site2241.net/november2014.htm