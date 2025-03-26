# 🌲🔥 Forest Fire & Heatwave Detection System

## 📌 Project Overview
This project is designed to detect **forest fires** and **heatwaves** using an **ESP32, ESP32-CAM, MQ sensor (alcohol sensor), and a servo motor**. The system scans an area for fire, detects smoke or heatwaves, and triggers an alert.

## 🛠 Components Used
- **ESP32** - Main microcontroller
- **ESP32-CAM** - Captures images for AI-based fire detection
- **Servo Motor** - Rotates the ESP32-CAM for scanning
- **MQ Sensor (Alcohol Sensor)** - Detects smoke & heatwave-related air quality changes
- **Hairdryer** (for testing heatwave detection)
- **WiFi (optional for remote alerts)**

## 🚀 Features
- 🔥 **Fire Detection**: Uses AI-based image recognition
- 🌡️ **Heatwave Detection**: Senses air quality changes using an MQ sensor
- 💨 **Smoke Detection**: Detects gases associated with fires
- 🎥 **Servo-Based Scanning**: Rotates the camera to monitor different angles
- ⚠️ **Alerts**: Triggers an alarm when fire or heat is detected

## 🛠 Setup & Wiring
### **ESP32-CAM + Servo Motor (Fire Scanning)**
| Component  | ESP32-CAM Pin |
|------------|--------------|
| Servo Signal | GPIO 13 |
| Servo VCC | 3.3V / 5V |
| Servo GND | GND |

### **MQ Sensor (Heatwave Detection)**
| MQ Sensor Pin | ESP32 Pin |
|--------------|-----------|
| VCC | 3.3V / 5V |
| GND | GND |
| A0 (Analog Output) | GPIO 34 |

## 🔥 Fire Detection Code (ESP32-CAM + Servo)
```cpp
#include <ESP32Servo.h>

Servo camServo;
int pos = 0;

void setup() {
  Serial.begin(115200);
  camServo.attach(13);  // Servo connected to GPIO13
}

void loop() {
  for (pos = 0; pos <= 180; pos += 10) {  // Move servo left-right
    camServo.write(pos);
    delay(500);
    Serial.println("Scanning area...");
    // AI-based fire detection code goes here (future step)
  }
}
```

## 🌡️ Heatwave Detection Code (MQ Sensor + ESP32)
```cpp
#define MQ_SENSOR 34  // Analog pin for MQ sensor

void setup() {
  Serial.begin(115200);
  pinMode(MQ_SENSOR, INPUT);
}

void loop() {
  int airQuality = analogRead(MQ_SENSOR); // Read sensor value
  Serial.print("Air Quality Level: ");
  Serial.println(airQuality);

  if (airQuality > 600) {  // Threshold for heatwave detection
    Serial.println("🔥 Heatwave Detected! Alert Triggered!");
  }

  delay(1000);  // Wait for 1 second before next reading
}
```

## 📌 How to Test
### 🔥 Fire Detection Test
1. Upload and run the **ESP32-CAM + Servo code**.
2. Observe camera rotation and image capture.
3. (Next step: AI-based fire detection using Teachable Machine).

### 🌡️ Heatwave Detection Test
1. Upload and run the **MQ sensor code**.
2. Observe air quality levels on the **Serial Monitor**.
3. Use a **hairdryer** to simulate heat; check if values increase.
4. If air quality **> 600**, heatwave detected! 🔥

## 📢 Future Improvements
- ✅ **AI Fire Detection** (Teachable Machine + ESP32-CAM)
- ✅ **WiFi-Based Remote Alerts**
- ✅ **LoRa or GSM Integration for Alerts**
- ✅ **Buzzer or Water Pump Activation**

## 📌 Conclusion
This project provides an **ESP32-based solution** for detecting **forest fires** and **heatwaves** using AI and sensors. It can be expanded with remote alerts and advanced AI models.

Let's make **forests safer** with AI and IoT! 🌲🔥🚀

---

## 📜 License
This project is licensed under the [MIT License](LICENSE).

## 🤝 Contributing
Contributions are welcome! Feel free to fork the repository and submit a pull request.

## 📧 Contact
For any questions or collaborations, feel free to reach out!
- **GitHub**: ankit071105
- **Email**: kumarankit11458@gmail.com

