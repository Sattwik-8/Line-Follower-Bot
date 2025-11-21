# 7-Channel Line Follower Bot (Arduino)

A fully functional **Arduino-based line follower robot** designed to follow a black line on a white surface using a **7-channel IR sensor array**. This project demonstrates **sensor interfacing, motor control, and embedded systems programming**.

---

## Features

- **7-channel IR sensor array** for precise line detection  
- **PID-like movement control** (basic proportional response to line deviation)  
- **Dual DC motors** with motor driver (L298N / L293D)  
- Real-time **line tracking** for smooth navigation  
- **Compact and modular hardware design**  
- Fully simulated in software (optional) or built in hardware  

---

## Components Used

| Component         | Quantity |
|------------------|----------|
| Arduino Uno       | 1        |
| 7-Channel IR Sensor Array | 1 |
| DC Motors         | 2        |
| Motor Driver (L298N/L293D) | 1 |
| Wheels            | 2        |
| Chassis           | 1        |
| Jumper Wires      | Several  |
| Power Supply / Battery | 1 |

---

## Wiring / Pin Mapping

| Arduino Pin | Component         |
|------------|------------------|
| Digital Pins 2–8 | IR sensor inputs (depends on wiring) |
| Digital Pins 9, 10 | Motor driver IN1 & IN2 (Motor A) |
| Digital Pins 11, 12 | Motor driver IN3 & IN4 (Motor B) |
| PWM Pins 3, 5 | Enable pins for speed control (Motor A & B) |
| GND, 5V | Power and common ground |

> Adjust pins according to your setup and motor driver.  

---

## How It Works

1. **Sensors Read Line**: IR sensors detect black line on white surface.  
2. **Decision Logic**: Arduino reads sensor states and decides motor actions:  
   - Line centered → move forward  
   - Line left → turn left  
   - Line right → turn right  
3. **Motor Control**: Motor driver controls speed and direction of DC motors to correct path.  
4. **Continuous Tracking**: Robot follows line until the path ends.  

---

## Code

Core logic includes:

- Reading 7-channel IR sensor array  
- Determining line deviation  
- Controlling motor speed and direction via motor driver  

```cpp
// Example snippet
int sensorValues[7];
for(int i=0;i<7;i++){
  sensorValues[i] = digitalRead(sensorPins[i]);
}

// Basic logic for line following
if(sensorValues[3]==LOW){
  // Centered → forward
} else if(sensorValues[0]==LOW || sensorValues[1]==LOW){
  // Turn left
} else if(sensorValues[5]==LOW || sensorValues[6]==LOW){
  // Turn right
}

// Motor control via L298N
analogWrite(enA, speedA);
analogWrite(enB, speedB);
```
---

## 👤 Author

**Sattwik**  
