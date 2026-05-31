# ESP32 Worldwide Hacking Simulator

An immersive, retro-style cyberpunk terminal simulation designed for the **ESP32 Dev Module**. It uses an I2C OLED display driven by the highly optimized **u8g2** library to simulate a real-time global cyber-attack terminal right on your desk.

---

## 📌 Hardware Pinout Configuration

The OLED display connects to the ESP32 using the native hardware I2C bus pins. Connect your module according to this map:



| OLED Display Pin | ESP32 Dev Module Pin | Description / Function |
| :--- | :--- | :--- |
| **GND** | **GND** | System Ground Power |
| **VCC** | **3V3** | 3.3V Logic Power Input |
| **SCL** | **IO22 (GPIO 22)** | I2C Hardware Clock |
| **SDA** | **IO21 (GPIO 21)** | I2C Hardware Data |

---

## ⚙️ Display Compatibility

The software is configured out-of-the-box for **1.3-inch OLED displays** utilizing the **SH1106** driver chipset. 
- **Driver Support:** Because it relies on the universal `u8g2` graphics engine, this project is fully compatible with virtually any **SH1106** or **SSD1306** I2C OLED screen.
- **Resolution:** Supports both standard **132x64** and **128x64** pixel matrix displays.

---

## 🔧 Software Requirements & Initialization

To compile this simulation without errors, ensure your environment meets the following conditions:

1. **Arduino IDE** with the ESP32 board manager installed.
2. **u8g2 Library** by oliver (Install via the built-in Arduino Library Manager).
3. **IDE Board Configuration (Tools Menu):**
   - **Board:** `ESP32 Dev Module`
   - **PSRAM:** `Disabled`

### 💻 u8g2 Constructor Setup
Inside your main `.ino` sketch file, make sure your constructor line uses the hardware I2C wire profile. For a standard SH1106 128x64 screen, your constructor declaration should look like this:

```cpp
#include <Arduino.h>
#include <U8g2lib.h>
#include <Wire.h>

// Full page buffer hardware I2C constructor for SH1106 128x64
U8G2_SH1106_128X64_NONAME_F_HW_I2C u8g2(U8G2_R0, /* reset=*/ U8X8_PIN_NONE);
```
*(Note: If you are using an SSD1306 screen, simply change the constructor line to match your specific panel definition, such as `U8G2_SSD1306_128X64_NONAME_F_HW_I2C`).*

---

## 🕹️ Simulation Features & Core Loops

Once flashed, the ESP32 operates completely independently (no active internet connection required to run the simulation layout):
* **Cyberpunk Terminal UI:** Renders dynamic terminal output, scrolling code structures, data parsing logs, and progress indicators mimicking deep-system penetrations.
* **Global Target Vectors:** Automatically cycles through randomized international target nodes, spoofed IP generation protocols, and data extraction trackers.
* **High-Density Animation:** Utilizing full-page buffering (`_F_`), the software updates complex geometric layouts and text frames smoothly across the 64-pixel vertical space without annoying screen flicker.
INFORMATION: The "hacking" functions above is just a simulation and does not hack the real world.It doesn't even have to connect to the Internet!
