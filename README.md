# 🧠 Ultrasonic-Based Smart Dustbin for Contactless Waste Disposal 🗑️

## 📌 Table of Contents

1. [🌍 Problem Statement](#problem-statement)
2. [🚀 Project Overview](#project-overview)
3. [📦 Components Used](#components-used)
4. [⚙️ Working Principle](#working-principle)
5. [🔌 Circuit Diagram](#circuit-diagram)
6. [💻 Code Explanation](#code-explanation)
7. [📸 Images](#images)
8. [📈 Future Enhancements](#future-enhancements)
9. [🤝 Acknowledgements](#acknowledgements)

---

## 🌍 Problem Statement

In today’s world, hygiene and cleanliness are more important than ever. Touching dustbins increases the risk of germ transfer and infections 🤒, especially in public places. We need a **contactless solution** to promote a healthier environment 🧼🌱.

---

## 🚀 Project Overview

This project presents a **Smart Dustbin** that opens and closes automatically based on proximity sensing using an ultrasonic sensor (HC-SR04) and a servo motor. The system is powered by an Arduino Uno and displays live status updates on an LCD screen. 💡

> 👨‍💻 Built using **TinkerCAD**, **Arduino**, and a passion for solving real-world problems.

---

## 📦 Components Used

| Component                   | Quantity  |
| --------------------------- | --------- |
| Arduino Uno                 | 1         |
| Ultrasonic Sensor (HC-SR04) | 1         |
| Servo Motor (SG90/MG90)     | 1         |
| 16x2 LCD Display            | 1         |
| Potentiometer               | 1         |
| Breadboard                  | 1         |
| Jumper Wires                | As needed |
| USB Cable                   | 1         |

---

## ⚙️ Working Principle

1. 🔊 **Ultrasonic Sensor** measures the distance from the user's hand.
2. 🔁 If the hand is detected within 50 cm, the **servo motor** rotates to open the lid.
3. 🧠 A **16x2 LCD** displays the system status (`Dustbin opened` / `Dustbin closed`).
4. 🕒 The lid automatically closes after a short delay if no hand is detected.

---

## 🔌 Circuit Diagram

🖼️ Add the following image (your circuit diagram):



---

## 💻 Code Explanation

```cpp
#include <LiquidCrystal.h>
#include <Servo.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
Servo servo;
int trig = 10;
int echo = 9;

void setup() {
  lcd.begin(16, 2);
  Serial.begin(9600);
  servo.attach(7);
  servo.write(0);
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);

  lcd.setCursor(4, 0);
  lcd.print("WELCOME");
  delay(2000);
  lcd.clear();
  lcd.setCursor(1, 0);
  lcd.print("Smart Dustbin");
  delay(2000);
}

void loop() {
  digitalWrite(trig, LOW);
  delayMicroseconds(5);
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);

  int a = pulseIn(echo, HIGH);
  int distance = a * 0.0343 / 2;
  Serial.println(distance);

  if (distance < 50) {
    servo.write(90);
    lcd.clear();
    lcd.setCursor(1, 0);
    lcd.print("Dustbin opened");
    delay(500);
  } else {
    lcd.clear();
    lcd.setCursor(1, 0);
    lcd.print("Dustbin closed");
    delay(500);
    servo.write(0);
  }
}
```

### 🔍 Key Functions:

* `pulseIn()`: Measures time for echo.
* `lcd.print()`: Displays text on the LCD.
* `servo.write(angle)`: Controls servo motor for lid.

---

## 📸 Images

---

## 📈 Future Enhancements

✅ Add IR sensor for better precision
✅ Use IoT (like ESP32) to track bin usage in real-time
✅ Solar power for eco-friendly operation ☀️
✅ Add voice output using a speaker 🔊

---

## 🤝 Acknowledgements

Thanks to platforms like **TinkerCAD**, **Arduino**, and the open-source community for making learning electronics fun and accessible! 🙌

