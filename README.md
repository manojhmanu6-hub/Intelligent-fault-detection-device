# Intelligent Fall Detection System Using ESP32

## 📌 Project Overview
The **Intelligent Fall Detection System** is an IoT-based safety device designed to detect accidental falls and immediately notify a registered emergency contact through SMS.

The system uses an ESP32 DevKit V1, MPU6050 accelerometer and gyroscope, GPS module, and A7670C GSM module to monitor movement, detect falls, and share the person's location.

## ✨ Features
- **Three-Trigger Fall Detection:** Detects falls using low acceleration, high acceleration, and gyroscope measurements.
- **Motion Monitoring:** Uses MPU6050 to measure acceleration and angular velocity.
- **GPS Tracking:** Retrieves latitude and longitude coordinates.
- **SMS Emergency Alerts:** Sends fall notifications with a Google Maps location link.
- **LCD Display:** Displays real-time system and sensor status.
- **Buzzer Alarm:** Activates an alarm when a fall is detected.
- **Push Button:** Allows the user to acknowledge the alarm.
- **Belt Monitoring:** Hall Effect sensor checks whether the safety belt is closed.
- **Human Detection:** Capacitive sensor verifies human contact before enabling fall detection.

## 🛠️ Hardware Requirements
| Component | Purpose |
|---|---|
| ESP32 DevKit V1 | Main controller |
| MPU6050 | Accelerometer and gyroscope |
| A7670C GSM Module | SMS communication |
| GPS Module | Location tracking |
| 16x2 I2C LCD | Status display |
| Buzzer | Emergency alarm |
| Push Button | Alarm acknowledgement |
| Hall Effect Sensor | Belt detection |
| Capacitive Sensor | Human/contact detection |
| Connecting Wires | Circuit connections |

## 💻 Software Requirements
- Arduino IDE
- ESP32 Board Package
- Wire Library
- LiquidCrystal_I2C Library
- TinyGPSPlus Library
- HardwareSerial Library

## 🔌 Pin Configuration

| Component | ESP32 GPIO |
|---|---|
| GPS RX | 19 |
| GPS TX | 23 |
| GSM RX | 18 |
| GSM TX | 15 |
| I2C SDA | 21 |
| I2C SCL | 22 |
| Buzzer | 5 |
| Push Button | 14 |
| Hall Effect Sensor | 13 |
| Capacitive Sensor | 27 |

**MPU6050 and LCD:** Both use the shared I2C communication bus.

## ⚙️ Working Principle

The system operates through the following steps:

1. **System Initialization:** ESP32 initializes the GPS, GSM, LCD, MPU6050, and other sensors.
2. **Belt Verification:** Hall Effect sensor checks whether the belt is properly closed.
3. **Human Detection:** Capacitive sensor verifies human contact.
4. **Motion Monitoring:** MPU6050 continuously measures acceleration and gyroscope values.
5. **Fall Detection:** The system checks three conditions:
   - Trigger 1: Low acceleration (Amp ≤ 2).
   - Trigger 2: High acceleration (Amp ≥ 12).
   - Trigger 3: Gyroscope magnitude between 30 and 400.
6. **Fall Confirmation:** The system checks whether the orientation stabilizes.
7. **Emergency Alert:** Buzzer activates and SMS is sent through the A7670C module.
8. **Location Sharing:** GPS coordinates and Google Maps link are included in the alert.
9. **Alarm Acknowledgement:** The user can press the button to stop the buzzer and restart monitoring.

## 🔄 System Workflow

```text
       SYSTEM START
            |
            v
    Initialize ESP32
            |
            v
   Initialize All Sensors
            |
            v
      Check Belt Status
            |
       Belt Closed?
        /       \
      No         Yes
      |           |
   Wait       Detect Human
                  |
             Human Found?
              /      \
            No        Yes
            |          |
          Wait     Read MPU6050
                       |
                 Trigger 1
                 Low Acceleration
                       |
                 Trigger 2
                 High Acceleration
                       |
                 Trigger 3
                 Gyroscope Check
                       |
                 Confirm Fall
                       |
                Activate Buzzer
                       |
                Get GPS Location
                       |
                  Send SMS
                       |
                Button Pressed?
                       |
                Stop Buzzer
                       |
                 Resume Monitoring
```

## 📩 Sample Emergency SMS

```text
FALL DETECTED! Check person immediately.
Lat:12.xxxxxx
Lon:77.xxxxxx
Map:https://maps.google.com/?q=12.xxxxxx,77.xxxxxx
```

## 🚀 Installation and Execution

1. Install Arduino IDE.
2. Install the ESP32 board package.
3. Install the required Arduino libraries.
4. Connect all hardware components according to the pin configuration.
5. Open the Arduino source code.
6. Update the emergency contact number in `ADMIN_NUMBER`.
7. Select ESP32 DevKit V1 from the Arduino board menu.
8. Select the appropriate COM port.
9. Upload the program.
10. Open Serial Monitor at **115200 baud**.

Type `S` in the Serial Monitor to send a test SMS.

## 🔮 Future Enhancements
- Mobile application integration.
- Cloud-based health and activity monitoring.
- Real-time emergency notifications.
- Fall detection using machine learning.
- Battery monitoring and power optimization.

## ⚠️ Disclaimer
This is an academic IoT prototype. It should not be considered a certified medical or emergency-response device. Sensor calibration, hardware testing, network availability, and real-world validation are necessary before practical deployment.

## 👩‍💻 Project Information
**Project Name:** Intelligent Fall Detection System  
**Platform:** ESP32  
**Domain:** Internet of Things (IoT), Embedded Systems and Safety Monitoring  
**Programming Language:** Embedded C/C++
