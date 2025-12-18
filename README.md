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

install ExpressIF from the Libraries then select ESP-S3-BOX
then make sure you have this for the OLED libraries
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

and the SDA is pin 41 and the SCL is pin 42.

commonly the address is 0x3C you can check it by using an address checker for I2C
the just upload the code

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





