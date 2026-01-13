# STM32 Light Control with BH1750

Microcontroller-based light control system using an STM32 microcontroller, BH1750 digital light sensor (I2C) and LED (PWM/digital control).  
The system reads ambient light in lux and controls LED brightness (or ON/OFF) to keep the light level close to a target value.

---

## Features

- Ambient light measurement in **lux** using **BH1750** (I2C)
- LED control:
  - **PWM brightness control** (recommended) or **ON/OFF**
- Adjustable setpoint (target lux) and thresholds
- UART monitoring (optional): print lux value and LED duty cycle
- Modular firmware structure (drivers / app logic)

---

## Hardware

- STM32 NUCLEO development board (your board model)
- BH1750 light sensor module
- LED + resistor (or external LED driver / MOSFET for мощный LED)
- Breadboard + jumper wires

### Wiring (example)

**BH1750 → STM32 (I2C)**  
- VCC → 3.3V  
- GND → GND  
- SDA → I2C SDA pin  
- SCL → I2C SCL pin  

**LED**
- LED anode → PWM pin (through resistor)  
- LED cathode → GND  

> Note: If you use a high power LED, connect it via MOSFET driver (do not power it directly from MCU pin).

---

## Software

- STM32CubeIDE
- STM32 HAL drivers
- C language

---

## How it works

1. STM32 reads light level from BH1750 (lux).
2. Compares lux with a target value (setpoint).
3. Updates LED state:
   - PWM duty increases when the environment is dark
   - PWM duty decreases when the environment is bright

---

## Repository structure (example)

```text
/Core
  /Inc
  /Src
/Drivers
README.md
