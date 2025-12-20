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
# XiaoZhi ESP32 – English Setup Guide

This guide explains how to flash, configure, and use **XiaoZhi ESP32** with English support.

---

## 🔗 Project Link (English Translation)

Official repository with English translation:  
👉 https://github.com/78/xiaozhi-esp32

---

## ✅ Working Firmware Version

Use the following firmware:


Flash it using the **flasher tool** found inside the **merge_bin** folder.

---

## 🔥 Flashing the Firmware

1. Open the flasher tool.
2. Select the firmware:

3. Flash the ESP32.
4. After flashing, the device will automatically start testing.

---

## 🎤 Button Functions

- **Short press BOOT button**  
→ Records audio and repeats it.

- **Long press BOTH buttons**  
→ Enters **Wi-Fi pairing mode**  
→ Device freezes briefly  
→ Then displays an **IP address**

---

## 📡 Wi-Fi Configuration

The ESP32 creates its **own Wi-Fi hotspot**.

### Steps:
1. On your phone, connect to the **ESP32 hotspot**.
2. Open the setup page.
3. Enter your Wi-Fi details:
- **Wi-Fi Name (SSID)**
- **Wi-Fi Password**

⚠️ **Important Notes:**
- ❌ **5G Wi-Fi is NOT supported**
- ✅ Use **2.4G / 4G Wi-Fi only**

---

## 🌐 Account & Agent Setup

1. Go to:  
👉 https://xiaozhi.me/
2. Log in using **Gmail** or another supported method.
3. You will see a **6-digit code**.
4. Use this code to **create an agent**.

### Reference Screenshots

<img width="700" height="250" alt="Agent Code" src="https://github.com/user-attachments/assets/41fe8fc6-4aa5-4db8-b82c-9b288479e6f8" />

<img width="500" height="250" alt="Agent Setup" src="https://github.com/user-attachments/assets/3608043b-a7cc-4576-b490-87e77e806d3d" />

---

## 🌍 Change Language to English

By default, the interface and dialogue are in **Chinese**.

### To switch to English:
1. Open the **Customization / Settings** page.
2. Change the **dialogue language** to **English**.
3. Save the settings.

### Screenshots

<img width="607" height="362" alt="Language Settings" src="https://github.com/user-attachments/assets/a03a16c1-8cd1-470d-bff3-f6e8cc4c248f" />

<img width="1064" height="495" alt="Dialogue Settings" src="https://github.com/user-attachments/assets/72456c31-e562-4bfc-bbfb-8f0a07ae8e96" />

✅ The device will now speak **English**.  
You can explore other customization options if you want.

---

## 📌 Notes

- Ensure a stable power supply for the ESP32
- Always use **2.4G Wi-Fi**
- If the device freezes, reboot and re-enter pairing mode

---
