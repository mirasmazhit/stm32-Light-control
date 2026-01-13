# STM32 Light Control with BH1750

Microcontroller-based light control system using an STM32 microcontroller, BH1750 digital light sensor (I2C) and LED (PWM/digital control).  
The system reads ambient light in lux and controls LED brightness (or ON/OFF) to keep the light level close to a target value.

---

## Features

- Ambient light measurement in **lux** using **BH1750** 
- LED control:
  - **PWM brightness control**  or **ON/OFF**
- Adjustable setpoint (target lux) and thresholds
- UART monitoring (optional): print lux value and LED duty cycle
- Modular firmware structure (drivers / app logic)

---

## Hardware

- STM32 NUCLEO development board 
- BH1750 light sensor module
- LED + resistor 
- Breadboard + jumper wires



## Software

- STM32CubeIDE
- STM32 HAL drivers
- C language
