# Qlockthree

This is a fork of [Qlockthree](https://github.com/bracci/Qlockthree) adapted for the [CLT 2.0](http://www.leuchtbildshop.net/epages/64015097.sf/de_DE/?ObjectPath=/Shops/64015097/Products/CLT2-RL/SubProducts/CLT2-RL-01) and a front with same [layout as used by the `mikrocontroller.net` forum](https://www.mikrocontroller.net/articles/Datei:Wordclock-frontplatte-v2.png).

If you don't feel like compiling the firmware yourself, this repository also contains a compiled firmware that can be flashed via ISP: [Firmware download](Qlockthree.hex)

In order to flash the firmware with an ISP programmer, a simple breadboard setup is sufficient: connect the ISP pins (MISO, MOSI, SCK, RESET, VCC, GND), connect a 16 MHz crystal between pins 9 and 10, and also connect pins 9 and 10 to GND with a 22 pF ceramic capacitor each.


## Short installation guide:

In order to get the firmware compile you have to install following libraries:

from Arduino Library Manager (guide: https://www.arduino.cc/en/Guide/Libraries):
* [NeoPixel library](https://github.com/adafruit/Adafruit_NeoPixel)
* [DotStar library](https://github.com/adafruit/Adafruit_DotStar)
* [LPD8806 library](https://github.com/adafruit/LPD8806)
* [LedControl (MAX7219) library](https://github.com/wayoda/LedControl)

others you have to install/copy manually to your library directory (C:\Users\MyUserName\Documents\Arduino\libraries\):
* [LPD8806DBL library](https://github.com/bracci/LPD8806DBL) (find download button on the right "Download ZIP")(only used for XXL-matrix using 2 LED each letter)
* [LPD8806RGBW library](https://github.com/bracci/LPD8806RGBW) (find download button on the right "Download ZIP")(only used for LPD8806 RGBW LED's)

P.S.: Unfortunately the LPD8806 library from Adafruit includes a bug which prevents from successfully compile the sketch.
You have to open the file "LPD8806.h" from "C:\Users\MyUserName\Documents\Arduino\libraries\LPD8806" and paste the following lines after file header:

```
#ifndef __LPD8806__H__
#define __LPD8806__H__
```

At the end of the file close the hash-if:
```
#endif
```

After this adaption the class should look somehow like that:
```
[... header...]
#ifndef __LPD8806__H__
#define __LPD8806__H__

class LPD8806 {
[... class content...]
};

#endif
```
