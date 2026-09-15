# Arduino & ESP32 Starter Codes, Circuits & Pinouts ⚡

> Tested boilerplate code snippets, circuit pinout tables, and practical projects for Arduino, ESP32, and Raspberry Pi makers by [Educational Engineering Team](https://www.lucebra.com/instructor/educationalengineeringteam) on [Lucebra](https://www.lucebra.com).

[![Lucebra Platform](https://img.shields.io/badge/Platform-Lucebra.com-2563eb.svg)](https://www.lucebra.com)
[![Hardware Verified](https://img.shields.io/badge/Hardware-ESP32%20%7C%20Arduino%20Uno-10b981.svg)](https://www.lucebra.com)
[![350+ Video Projects](https://img.shields.io/badge/Video%20Courses-350%2B%20Tracks-orange.svg)](https://www.lucebra.com/instructor/educationalengineeringteam)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Google Play](https://img.shields.io/badge/Google_Play-Download-34a853.svg?logo=google-play&logoColor=white)](https://play.google.com/store/apps/details?id=com.lucebra.app)
[![App Store](https://img.shields.io/badge/App_Store-iOS-000000.svg?logo=apple&logoColor=white)](https://apps.apple.com/us/app/lucebra/id6754839631)

---

## 🎁 Exclusive Maker & Team Perks

| Coupon Code | Exclusive Offer & Perk | Target Plan | Direct Activation Link |
| :--- | :--- | :--- | :--- |
| **`BB30TRIAL`** | **Extended 30-Day Free Trial** (Full access, unlimited seats) | Lucebra Business | [👉 Activate 30-Day Trial](https://www.lucebra.com/business-checkout?coupon=BB30TRIAL) |
| **`LCBR25EB`** | **50% OFF Lifetime Discount + 7-Day Free Trial** | Lucebra Business | [👉 Activate 50% Off Deal](https://www.lucebra.com/business-checkout?coupon=LCBR25EB) |

---

## 🔌 Quick Reference Pinouts

### ESP32 DevKit V1 Pinout Table
| Pin Name | Function | ADC / DAC | PWM / Touch | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **GPIO 2** | Built-in Blue LED | ADC2_CH2 | Touch 2 | Pull-down on boot |
| **GPIO 4** | General I/O | ADC2_CH0 | Touch 0 | Safe for sensors |
| **GPIO 21** | I2C SDA | - | - | Wire data line |
| **GPIO 22** | I2C SCL | - | - | Wire clock line |
| **GPIO 34** | Input Only | ADC1_CH6 | - | No internal pull-up |
| **GPIO 35** | Input Only | ADC1_CH7 | - | Perfect for analog sensors |

---

## 💻 Tested Code Boilerplates

### 1. ESP32 WiFi Scanner & Connector
```cpp
#include <WiFi.h>

const char* ssid = "YOUR_WIFI_SSID";
const char* password = "YOUR_WIFI_PASSWORD";

void setup() {
  Serial.begin(115200);
  delay(1000);

  Serial.println("Connecting to WiFi...");
  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("
WiFi Connected!");
  Serial.print("IP Address: ");
  Serial.println(WiFi.localIP());
}

void loop() {
  // Your IoT logic here
}
```
> 🎓 **Master this in depth:** [Program ESP32 without Coding](https://www.lucebra.com/courses/program-esp32-without-coding)

---

### 2. DHT11 / DHT22 Temperature & Humidity Sensor
```cpp
#include <DHT.h>

#define DHTPIN 4
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  delay(2000);
  float h = dht.readHumidity();
  float t = dht.readTemperature();

  if (isnan(h) || isnan(t)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }

  Serial.print("Humidity: "); Serial.print(h); Serial.print(" %	");
  Serial.print("Temperature: "); Serial.print(t); Serial.println(" *C");
}
```
> 🎓 **Full Video Course:** [ESP32 Email Alert Based on Sensors Reading](https://www.lucebra.com/courses/esp32-email-alert-based-on-sensors-reading)

---

### 3. I2C 0.96\" OLED Display (SSD1306)
```cpp
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64

Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, -1);

void setup() {
  Serial.begin(115200);
  if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
    Serial.println(F("SSD1306 allocation failed"));
    for(;;);
  }
  display.clearDisplay();
  display.setTextSize(1);
  display.setTextColor(WHITE);
  display.setCursor(10, 20);
  display.println("Hello, Lucebra!");
  display.display();
}

void loop() {}
```
> 🎓 **Full Hands-On Track:** [SD Card Interfacing with Arduino](https://www.lucebra.com/courses/sd-card-interfacing-with-arduino)

---

## 🏆 Official Instructor Catalog
All 350+ embedded courses by Ashraf Said AlMadhoun are indexed at:  
👉 [**Lucebrallc/awesome-educational-engineering-team-courses**](https://github.com/Lucebrallc/awesome-educational-engineering-team-courses)

---

---

## 📱 Learn on the Go — Official Lucebra Mobile Apps

Study anytime, anywhere with offline video streaming, audio mode, quiz practice, and instant verifiable certificates on iOS and Android:

| Platform | Direct Store Link | Availability |
| :--- | :--- | :---: |
| 🍏 **Apple App Store (iOS & iPadOS)** | [👉 **Download on the App Store**](https://apps.apple.com/us/app/lucebra/id6754839631) | Free Download |
| 🤖 **Google Play Store (Android)** | [👉 **Get it on Google Play**](https://play.google.com/store/apps/details?id=com.lucebra.app) | Free Download |

---

© Lucebra Global Education. Visit [lucebra.com](https://www.lucebra.com).
