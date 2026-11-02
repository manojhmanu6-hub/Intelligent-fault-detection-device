# Intelligent Fall Detection Device

<p align="center">
  <a href="https://github.com/manojhmanu6-hub/Intelligent-fault-detection-device">
    <img src="https://img.shields.io/badge/GitHub-Repository-black?style=for-the-badge&logo=github" alt="GitHub Repository">
  </a>
  <img src="https://img.shields.io/badge/Platform-ESP32-blue?style=for-the-badge&logo=espressif" alt="ESP32">
  <img src="https://img.shields.io/badge/Domain-IoT-green?style=for-the-badge" alt="IoT">
  <img src="https://img.shields.io/badge/Language-C%2B%2B-orange?style=for-the-badge&logo=cplusplus" alt="C++">
</p>

## 📌 Project Overview

The **Intelligent Fall Detection Device** is an IoT-based safety monitoring system designed to detect accidental falls and send emergency notifications to registered contacts.

The device uses an ESP32 microcontroller integrated with an MPU6050 accelerometer and gyroscope, GPS module, GSM module, LCD display, and other sensors.

When a fall is detected, the system activates a buzzer and sends an SMS alert containing the person's GPS location to an emergency contact.

## 🎯 Objectives

- Detect accidental falls automatically.
- Monitor body movement using motion sensors.
- Identify whether the safety belt is properly closed.
- Verify human contact before enabling fall detection.
- Send emergency SMS notifications.
- Share the person's location through GPS.
- Provide immediate audio and visual alerts.

## ✨ Key Features

1. **Three-Trigger Fall Detection:** Uses acceleration and gyroscope measurements to identify potential falls.
2. **Real-Time Motion Monitoring:** Continuously reads MPU6050 sensor data.
3. **GPS Location Tracking:** Retrieves latitude and longitude coordinates.
4. **GSM Communication:** Sends emergency SMS using the A7670C module.
5. **LCD Display:** Displays sensor status and fall detection information.
6. **Buzzer Alert:** Activates an alarm when a fall is confirmed.
7. **Push Button Acknowledgement:** Allows the user to stop the active alarm.
8. **Belt Detection:** Uses a Hall Effect sensor to verify belt closure.
9. **Human Contact Detection:** Uses a capacitive sensor to verify contact.

## 🛠️ Hardware Components

| Component | Description |
|---|---|
| ESP32 DevKit V1 | Main microcontroller |
| MPU6050 | Accelerometer and gyroscope |
| A7670C GSM Module | Emergency SMS communication |
| GPS Module | Location tracking |
| 16×2 I2C LCD | Information display |
| Buzzer | Audio alert |
| Push Button | Alarm acknowledgement |
| Hall Effect Sensor | Belt status detection |
| Capacitive Sensor | Human/contact detection |
| Jumper Wires | Hardware connections |

## 💻 Software Requirements

- Arduino IDE
- ESP32 Board Package
- Embedded C/C++
- Wire Library
- LiquidCrystal_I2C Library
- TinyGPSPlus Library
- HardwareSerial Library

## 🔌 Pin Configuration

| Component | ESP32 GPIO |
|---|---|
| GPS RX | GPIO 19 |
| GPS TX | GPIO 23 |
| GSM RX | GPIO 18 |
| GSM TX | GPIO 15 |
| I2C SDA | GPIO 21 |
| I2C SCL | GPIO 22 |
| Buzzer | GPIO 5 |
| Push Button | GPIO 14 |
| Hall Effect Sensor | GPIO 13 |
| Capacitive Sensor | GPIO 27 |

**Note:** MPU6050 and LCD share the I2C communication bus. The LCD address is configured as `0x27` in the source code.

## ⚙️ Working Principle

### 1. System Initialization
The ESP32 initializes all connected sensors and communication modules, including GPS, GSM, MPU6050, and LCD.

### 2. Belt Status Detection
The Hall Effect sensor checks whether the safety belt is properly closed.

### 3. Human Detection
The capacitive sensor verifies human contact. Fall detection is enabled only when both belt and contact conditions are satisfied.

### 4. Motion Monitoring
The MPU6050 continuously measures acceleration and angular velocity.

### 5. Three-Trigger Fall Detection

- **Trigger 1 – Low Acceleration:** Detects a sudden reduction in acceleration.
- **Trigger 2 – High Acceleration:** Identifies a sudden acceleration increase.
- **Trigger 3 – Gyroscope Measurement:** Checks angular movement to identify possible falling motion.

### 6. Fall Confirmation
The system checks the final gyroscope measurement to confirm whether the person's orientation has stabilized.

### 7. Emergency Notification
After confirming a fall:
- The buzzer is activated.
- GPS coordinates are retrieved.
- An emergency SMS is sent through the GSM module.
- The LCD displays the fall detection and SMS status.

### 8. Alarm Acknowledgement
The push button allows the user to acknowledge the alarm, switch off the buzzer, and restart monitoring.

## 🔄 System Workflow

```text
          SYSTEM START
                |
                v
       Initialize ESP32
                |
                v
       Initialize Sensors
                |
                v
        Check Belt Status
                |
         Is Belt Closed?
           /        \
         No          Yes
         |            |
      Wait       Detect Human
                      |
                Human Detected?
                  /       \
                No         Yes
                |           |
              Wait      Read MPU6050
                            |
                            v
                    Trigger 1: Low
                     Acceleration
                            |
                            v
                    Trigger 2: High
                     Acceleration
                            |
                            v
                    Trigger 3: Gyroscope
                       Measurement
                            |
                            v
                      Confirm Fall
                            |
                            v
                     Activate Buzzer
                            |
                            v
                     Retrieve GPS Data
                            |
                            v
                       Send SMS
                            |
                            v
                    Button Acknowledgement
                            |
                            v
                    Resume Monitoring
```

## 📩 Sample Emergency SMS

```text
FALL DETECTED! Check person immediately.

Lat: 12.xxxxxx
Lon: 77.xxxxxx

Map: https://maps.google.com/?q=12.xxxxxx,77.xxxxxx
```

## 🚀 Installation and Setup

1. Download or clone this repository.
2. Install Arduino IDE.
3. Install the ESP32 board package.
4. Install the required Arduino libraries.
5. Connect all components according to the pin configuration.
6. Open the Arduino source code.
7. Configure the emergency contact number using `ADMIN_NUMBER`.
8. Select ESP32 DevKit V1 in Arduino IDE.
9. Select the correct COM port.
10. Upload the program to the ESP32.
11. Open Serial Monitor at **115200 baud**.

### Test SMS

Type `S` in the Serial Monitor to send a test SMS through the GSM module.

## 📂 Project Repository

**GitHub Repository:**

<a href="https://github.com/manojhmanu6-hub/Intelligent-fault-detection-device">Intelligent Fault Detection Device – View Source Code</a>

Clone the repository:

```bash
git clone https://github.com/manojhmanu6-hub/Intelligent-fault-detection-device.git
```

## 🔮 Future Enhancements

- Mobile application integration.
- Cloud-based data monitoring.
- Real-time emergency notifications.
- Machine learning-based fall detection.
- Battery status monitoring.
- Improved sensor calibration and accuracy.

## ⚠️ Disclaimer

This project is an academic IoT prototype intended for demonstration and learning purposes. It is not a certified medical device or a replacement for professional emergency monitoring systems.

## 👨‍💻 Project Details

| Category | Details |
|---|---|
| Project Title | Intelligent Fall Detection Device |
| Domain | Internet of Things (IoT) |
| Controller | ESP32 DevKit V1 |
| Programming Language | Embedded C/C++ |
| Communication | GSM and GPS |
| Sensors | MPU6050, Hall Effect and Capacitive Sensor |
| Development Environment | Arduino IDE |

---

<p align="center">
  <b>Intelligent Fall Detection Device – IoT-Based Safety Monitoring System</b>
  <br>
  Designed to improve safety through intelligent fall detection and emergency communication.
</p>
