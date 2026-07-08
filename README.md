# 🤖 PID Line Follower Robot using Arduino UNO

A high-performance **5-Sensor PID Line Follower Robot** built using an **Arduino UNO**, **Adafruit Motor Shield (AFMotor Library)**, and a **Pololu QTR-5RC Reflectance Sensor Array**.

The robot uses a **Proportional-Derivative (PD) controller** to continuously calculate the deviation from the line and adjust the speed of both motors for smooth and accurate line tracking.

---

## 📌 Features

- 🚗 5-channel Pololu QTR RC sensor array
- ⚡ PD (Proportional-Derivative) control algorithm
- 🔄 Automatic sensor calibration at startup
- 🎯 Smooth line following
- ⚙ Adjustable motor speed and PID parameters
- 📚 Uses Adafruit AFMotor library

---

# 🔧 Hardware Components

| Component | Quantity |
|-----------|----------|
| Arduino UNO | 1 |
| Adafruit Motor Shield V1 | 1 |
| Pololu QTR-5RC Sensor Array | 1 |
| DC Geared Motors | 2 |
| Robot Chassis | 1 |
| Wheels | 2 |
| Caster Wheel | 1 |
| Battery Pack (7.4V–12V) | 1 |
| Power Switch | 1 |

---

# 📚 Libraries Used

```cpp
#include <PololuQTRSensors.h>
#include <AFMotor.h>
```

Install these libraries using the **Arduino Library Manager** before uploading the code.

---

# 🔌 Pin Configuration

## QTR-5RC Sensor Array

| Sensor | Arduino Pin |
|--------|-------------|
| S1 | A4 (Digital 18) |
| S2 | A3 (Digital 17) |
| S3 | A2 (Digital 16) |
| S4 | A1 (Digital 15) |
| S5 | A0 (Digital 14) |
| IR Emitter | D2 |

### Motor Connections

Motor control is handled through the **Adafruit Motor Shield**.

| Motor | Shield Port |
|-------|-------------|
| Left Motor | M1 |
| Right Motor | M2 |

---

# ⚙ PID Parameters

```cpp
#define KP 0.2
#define KD 5

#define M1_DEFAULT_SPEED 50
#define M2_DEFAULT_SPEED 50

#define M1_MAX_SPEED 70
#define M2_MAX_SPEED 70
```

These parameters can be tuned depending on:

- Motor RPM
- Robot Weight
- Wheel Diameter
- Track Type

---

# 🚀 Working Principle

1. Robot powers ON.
2. Sensor array performs automatic calibration.
3. QTR sensor reads the position of the black line.
4. Position error is calculated.

### Error Calculation

```text
Error = Current Position - Center Position
```

For a 5-sensor array,

```text
Center Position = 2000
```

### PD Controller

```text
Motor Correction =
KP × Error +
KD × (Current Error − Previous Error)
```

### Motor Speed Update

```text
Left Motor Speed  = Base Speed + Correction

Right Motor Speed = Base Speed - Correction
```

The robot continuously adjusts both motor speeds to remain centered on the line.

---

# 📈 Sensor Calibration

During startup:

```cpp
manual_calibration();
```

The robot samples the surface **250 times** to calculate:

- Minimum sensor values
- Maximum sensor values

These values are used to normalize the sensor readings for reliable line detection.

---

# 💻 Code Structure

```text
setup()
│
├── Delay
├── manual_calibration()
└── Stop Motors

loop()
│
├── Read Sensor Values
├── Calculate Line Position
├── Calculate Error
├── PD Controller
├── Compute Motor Speeds
└── Drive Motors
```

---

# 📁 Project Structure

```text
PID-Line-Follower/
│
├── PID_LineFollower.ino
├── README.md
├── LICENSE
├── images/
│   ├── Robot.jpg
│   ├── CircuitDiagram.png
│   ├── Working.gif
│   └── SensorArray.jpg
└── docs/
```

---

# 🧠 Algorithm

```text
               Start
                 │
                 ▼
      Initialize Arduino
                 │
                 ▼
       Initialize Motors
                 │
                 ▼
      Initialize QTR Sensors
                 │
                 ▼
      Perform Calibration
                 │
                 ▼
       Read Sensor Values
                 │
                 ▼
     Calculate Line Position
                 │
                 ▼
         Compute Error
                 │
                 ▼
        Apply PD Controller
                 │
                 ▼
 Update Left & Right Motor Speed
                 │
                 ▼
         Move the Robot
                 │
                 ▼
            Repeat Forever
```

---

# 📊 Performance

- ✅ Smooth line following
- ✅ Fast response to curves
- ✅ Stable motion
- ✅ Low oscillation
- ✅ Lightweight implementation
- ✅ Real-time sensor processing

---

# 🔮 Future Improvements

- Add Integral (I) term for full PID control
- Adaptive PID tuning
- Junction detection
- Maze solving
- Bluetooth control
- OLED display
- Wi-Fi monitoring
- Speed optimization
- Obstacle avoidance

---

# 👨‍💻 Author

**Manthan Dixit**

**B.Tech Computer Science & Engineering (IoT)**

**Arduino • Robotics • Embedded Systems • AI • Computer Vision**

---

# 📄 License

This project is licensed under the **MIT License**.

---

# 🙏 Acknowledgements

- Arduino
- Pololu Robotics
- Adafruit Motor Shield Library
- Open Source Robotics Community

---

## ⭐ If you found this project useful, consider giving it a Star on GitHub!
