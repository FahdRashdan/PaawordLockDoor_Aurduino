# 🔐 Arduino-Based Password Security System
### Digital Lock Implementation using Keypad Interfacing and Servo Actuation

👨‍💻 Authors: Fahd Rashdan & Belal Ehab  
🏫 Course: Computer Systems  
🏛 University: New Giza University (NGU)  
📅 Date: December 2025  

---

## 📌 Project Overview

This project presents a standalone digital door lock system built using an Arduino Uno.  
The system authenticates users using a secure 4-digit PIN entered through a 4x5 matrix keypad and controls a servo motor to physically lock or unlock a door.

A key feature of this system is the use of EEPROM memory, allowing the password to remain stored even after power loss.

This project demonstrates:

- Embedded systems design  
- Finite State Machine (FSM) logic  
- Hardware-software integration  
- Secure access control implementation  

---

## 🎯 Project Objectives

- Authenticate users using a 4-digit PIN  
- Control a physical locking mechanism (Servo Motor)  
- Provide visual feedback using a 16x2 LCD  
- Store password securely in EEPROM (non-volatile memory)  
- Allow password change with verification  

---

## 🏗 System Architecture

The system follows the Input → Process → Output (IPO) model.

### 🔹 Input
- 4x5 Matrix Membrane Keypad  
- User enters PIN or system commands  

### 🔹 Processing
- Arduino Uno (ATmega328P)
- Finite State Machine (FSM)
- EEPROM password verification  

### 🔹 Output
- 16x2 I2C LCD (User feedback)
- Servo Motor (0° = Locked, 90° = Unlocked)

---

## 🔩 Hardware Components

- Arduino Uno (ATmega328P)
- 4x5 Matrix Keypad
- Servo Motor (SG90 or similar)
- 16x2 LCD with I2C interface
- Breadboard
- Jumper wires

---

## 🔌 Wiring Configuration

### Keypad Wiring

| Keypad Wire | Function | Arduino Pin |
|-------------|----------|------------|
| Wire 1 | Row 1 | D2 |
| Wire 2 | Row 2 | D3 |
| Wire 3 | Row 3 | D4 |
| Wire 4 | Row 4 | D5 |
| Wire 5 | Row 5 | D6 |
| Wire 6 | Column 1 | D7 |
| Wire 7 | Column 2 | D8 |
| Wire 8 | Column 3 | D9 |
| Wire 9 | Column 4 | D11 |

### LCD Wiring (I2C)

| LCD Pin | Arduino |
|----------|----------|
| SDA | A4 |
| SCL | A5 |
| VCC | 5V |
| GND | GND |

### Servo Wiring

| Servo Pin | Arduino |
|------------|----------|
| Signal | D10 |
| VCC | 5V |
| GND | GND |

---

## 💻 Software Implementation

The software is written in C++ using the Arduino IDE.

### Libraries Used

```cpp
#include <Keypad.h>
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <Servo.h>
#include <EEPROM.h>
```

---

## 🧠 Finite State Machine (FSM)

The system operates using three states:

1. SETUP_NEW  
   - Create a new password (first-time use)

2. LOCKED  
   - Normal operation  
   - User enters PIN  
   - Option to change password  

3. VERIFY_OLD  
   - Verify old password before changing it  

This prevents invalid operations and ensures secure state transitions.

---

## 🔐 Key Features

- Password masked with `*` on LCD  
- 4-digit PIN validation  
- Password stored in EEPROM  
- Password change requires old PIN verification  
- Servo automatically locks after 3 seconds  
- Clear input using ESC key  
- Structured and modular code  

---

## 🧪 Testing Scenarios

### ✅ Scenario A – Access Granted
- Correct PIN entered  
- LCD displays: "Access Granted"  
- Servo rotates to 90°  
- Door unlocks for 3 seconds  
- Returns to locked position  

### ❌ Scenario B – Access Denied
- Incorrect PIN entered  
- LCD displays: "Access Denied"  
- Servo remains at 0°  

### 🔁 Scenario C – Password Change
- User presses 'A' (F1)  
- System requests old PIN  
- If correct → allows new PIN entry  
- New password saved in EEPROM  

---

## 🚀 How to Run the Project

1. Install Arduino IDE  
2. Install required libraries:
   - Keypad
   - LiquidCrystal_I2C
   - Servo (built-in)
3. Connect hardware as described  
4. Upload the code to Arduino Uno  
5. Power the system  
6. Create your 4-digit PIN  
7. System is ready to use  

---

## 📂 Repository Structure (Suggested)

```
Arduino-Password-Lock/
│
├── README.md
├── CODE.ino
├── Computer_Systems_Report.pdf
├── Presentation.pptx
└── images/
```

---

## 🔒 Security Notes

This system is a prototype-level embedded security system.  
For real-world deployment, improvements such as:

- Attempt limits and lockout timer  
- Encrypted password storage  
- Buzzer alarm  
- Intrusion detection  
- Metal casing  

can be implemented.

---

## 📜 Copyright & License

© 2025 Fahd Rashdan & Belal Ehab  
All Rights Reserved.

This project was developed as part of the Computer Systems course at New Giza University (NGU).

No part of this project may be reproduced, distributed, or used commercially without explicit written permission from the authors.

---

⭐ If you like this project, consider giving it a star on GitHub!
