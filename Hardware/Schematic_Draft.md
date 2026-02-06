# Preliminary Schematic Draft: ESP32 Micro-Drone 🚁

This document describes the connections needed to build the ESP32-based drone, inspired by the ESP-FLY project.

## 1. ESP32-WROOM-32 Pinout

| Peripheral | ESP32 Pin | Description |
|------------|-----------|-------------|
| **Motor 1 (FL)** | **GPIO 4** | PWM (Front-Left) via MOSFET |
| **Motor 2 (FR)** | **GPIO 33** | PWM (Front-Right) via MOSFET |
| **Motor 3 (RL)** | **GPIO 32** | PWM (Rear-Left) via MOSFET |
| **Motor 4 (RR)** | **GPIO 25** | PWM (Rear-Right) via MOSFET |
| **MPU6050 SDA** | **GPIO 21** | I2C Data |
| **MPU6050 SCL** | **GPIO 22** | I2C Clock |
| **V-Bat Monitor**| **GPIO 35** | Analog Input (via voltage divider) |

## 2. Motor Driver Circuit (MOSFET)
Each coreless motor must be driven by an N-channel MOSFET (e.g., **SI2302**):
- **Gate**: Connected to the GPIO pin via a 100 ohm resistor.
- **Source**: Connected to GND.
- **Drain**: Connected to the negative pole (-) of the motor.
- **Positive pole (+)** of the motor: Connected directly to V-Battery (3.7V).
- **Flyback Diode**: A 1N4148 diode in parallel with the motor to protect the MOSFET from voltage spikes.

## 3. Power and Sensors
- **Regulator**: MIC5219 (or similar) to generate clean 3.3V for ESP32 and MPU6050.
- **Capacitors**: Minimum 10uF at regulator input and output for stability.
- **IMU**: MPU6050 should be mounted as close to the center of the drone as possible.

## 4. Design Reference
The project uses the PCB itself as the frame to minimize weight. The PCB arms should be at least 4-5mm wide to withstand impacts.
