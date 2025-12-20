# ESP32XHS3E-AI
Resource guide cause the resources are in chinese
This is what it looks like
![176f8d1a-af2a-4fb7-a96d-0a06178c68e6](https://github.com/user-attachments/assets/e86162fa-5107-4e93-84d6-b952ec67d10a)

# FLASH METHOD
Follow the tutotial how to flash the ESP32-S3 
- https://jiayi0111.github.io/ESP32_S3-C3-extension-board-/Setting-up-Development-Enviroment/UsingFlashDownloadTooltoFlash.html
- https://youtu.be/ekStdti3eaQ?si=GDz-XLnRs952rwns
- https://xiaozhi.dev/en/docs/usage/firmware-download/


# chinese resource file to access bin files for the flashing procedures
- https://ai.feishu.cn/wiki/Zpz4wXBtdimBrLk25WdcXzxcnNS?fbclid
- https://ai.feishu.cn/wiki/W14Kw1s1uieoKjkP8N0c1VVvn8d


# Arduino IDE method

install ExpressIF from the Libraries then select ESP-S3-BOX then make sure you have this for the OLED libraries
- <Wire.h>
- <Adafruit_GFX.h>
-  <Adafruit_SSD1306.h>

and the SDA is pin 41 and the SCL is pin 42.

commonly the address is 0x3C you can check it by using an address checker for I2C then just upload the code

## CODE sample
**sketch_file*
```
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64
#define OLED_RESET -1

// Create display object
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

void setup() {
  Serial.begin(115200);

  // Initialize I2C (change pins if needed)
  Wire.begin(41, 42); // SDA, SCL

  // Initialize OLED
  if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) { // 0x3C is common OLED address
    Serial.println("SSD1306 allocation failed");
    while(1);
  }

  display.clearDisplay();
  display.setTextSize(2);
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0, 20);
  display.println("Hello!");
  display.display();
}

void loop() {
  // Nothing here, just display static text
}
```
# MORE UPDATES
Found english translation 
- https://github.com/78/xiaozhi-esp32
- click this

Working update

v2.0.5_bread-compact-wifi-128x64 select this then use the flasher 
from the file called merge bin.

you will see an it will run and do the testing in which if you press the button of the boot it will just record and repeat
so to get the network long press both of them to make it receieveable iand it will freeze then shows IP address

but to access that you will need to connect the esp32 device using the wifi network on your phone (THE ESP32 wil make its own hotspot) so you 
wiil nee to connect the hotspot

after that add your wifi network details( does not work on %G network) enter the 4G one
- wifi name
- wifi password

Then after that you must login in this website 
- https://xiaozhi.me/

login using gmail etc.

then at that moment you will see 6 digit numbers use those number to create the agent
<img width="700" height="250" alt="Screenshot 2025-12-20 135320" src="https://github.com/user-attachments/assets/41fe8fc6-4aa5-4db8-b82c-9b288479e6f8" />
<img width="500" height="250" alt="Screenshot 2025-12-20 135316" src="https://github.com/user-attachments/assets/3608043b-a7cc-4576-b490-87e77e806d3d" />


then don't foegt to translate in english since it is chinese in default 

customization of if you want it to speak english
<img width="607" height="362" alt="Screenshot 2025-12-20 135454" src="https://github.com/user-attachments/assets/a03a16c1-8cd1-470d-bff3-f6e8cc4c248f" />
click here 
<img width="1064" height="495" alt="Screenshot 2025-12-20 135530" src="https://github.com/user-attachments/assets/72456c31-e562-4bfc-bbfb-8f0a07ae8e96" />
change the dialogue into english and then your done (explore if you want)



