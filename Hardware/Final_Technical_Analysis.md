# Technical Analysis: Original ESP-FLY Project 🚁

Based on the analyzed source files (`main.c`, `motors.h`, `Kconfig.projbuild`), here is the hardware configuration of the original drone:

## 1. Pin Mapping (Standard ESP32)
| Function | GPIO Pin | Notes |
|----------|----------|------|
| **Motor 1 (Front-Left)** | **4** | PWM |
| **Motor 2 (Front-Right)** | **33** | PWM |
| **Motor 3 (Rear-Left)** | **32** | PWM |
| **Motor 4 (Rear-Right)** | **25** | PWM |
| **I2C SDA (IMU)** | **21** | For MPU6050 |
| **I2C SCL (IMU)** | **22** | For MPU6050 |
| **Blue LED** | **18** | Status |
| **Green LED** | **5** | Status |
| **Red LED** | **23** | Status |
| **Buzzer (+/-)** | **27 / 26**| Audio signals |

## 2. Firmware Architecture
- **Base**: ESP-IDF (Espressif IoT Development Framework).
- **Control**: RTOS system with dedicated tasks for:
    - Stabilization (PID Loop).
    - Wi-Fi Management.
    - Smartphone Command Reception.
- **Sensors**: MPU6050 integrated via I2C.

## 3. "Our" Customization Strategy
To make the project unique and improve it, I propose:
1. **Frame Design**: instead of a rectangular structure, we will use an **asymmetrical "X" design** that optimizes weight distribution and arm rigidity using the PCB.
2. **Power**: We will use **SI2302** MOSFETs (N-channel) which support higher currents for more powerful coreless motors (e.g., 720).
3. **Firmware**: We can add a custom **Web Dashboard** with telemetry indicators (battery level, real-time tilt) directly on the smartphone.
4. **Battery**: Integration of a **TP4056** charging circuit directly on the PCB for charging via micro-USB/USB-C without removing the battery.

## Next Steps
- [ ] Confirmation of pin selection.
- [ ] Start schematic drawing in KiCad/EasyEDA based on this map.
- [ ] Firmware adaptation to include telemetry.
