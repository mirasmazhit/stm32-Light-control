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

---

## Laboratory Context

This project is based on laboratory exercises for the course **Microprocessor Systems** at Poznań University of Technology and focuses on practical implementation of I²C communication with a digital light sensor BH1750. :contentReference[oaicite:0]{index=0}

The laboratory introduces:
- Structure and operation of the **I²C bus**
- Master–slave communication
- Sensor data acquisition using STM32 HAL
- Modular firmware design
- UART data transmission and monitoring :contentReference[oaicite:1]{index=1}

---

## BH1750 Digital Light Sensor

BH1750 is a digital ambient light sensor with:
- Measurement range: **1 – 65535 lux**
- Resolution: **1 lx or 4 lx**
- Interface: **I²C**
- Supply voltage: **3–5 V (3.3 V recommended)**  
- Built-in pull-up resistors on SDA and SCL lines :contentReference[oaicite:2]{index=2}

The sensor allows precise indoor and outdoor light measurement and is well suited for embedded control applications.

---

## I²C Communication

The system uses STM32 as **I²C Master** and BH1750 as **Slave** device.

- Two bus lines:
  - **SDA** – data line  
  - **SCL** – clock line  
- Communication handled using STM32 HAL functions:
  - `HAL_I2C_Master_Transmit()`
  - `HAL_I2C_Master_Receive()` :contentReference[oaicite:3]{index=3}

The first transmitted byte contains the slave address and transmission direction bit.

---

## Hardware Connection (NUCLEO-F746ZG)

| NUCLEO Pin | BH1750 Pin | Function |
|-----------|------------|----------|
| 3V3 | VCC | Power supply |
| GND | GND | Ground |
| PB8 (D15) | SCL | I²C clock |
| PB9 (D14) | SDA | I²C data |
| PA3 | LED driver gate (PWM) | LED brightness control | :contentReference[oaicite:4]{index=4}

---

## Firmware Tasks Implemented

According to laboratory scenario, the embedded application includes:

✔ I²C peripheral configuration  
✔ BH1750 initialization in continuous high-resolution mode  
✔ Periodic light measurement  
✔ Conversion of raw data to **lux**  
✔ UART transmission of measurement results  
✔ PWM control of LED brightness  
✔ Experimental measurement of LED–sensor static characteristics :contentReference[oaicite:5]{index=5}

---

## UART Monitoring

Serial communication allows sending measured lux values to PC.

Typical configuration:
- Baud rate: **9600 bps**
- 8 data bits
- No parity
- 1 stop bit :contentReference[oaicite:6]{index=6}



---

## Experimental Part

The system was used to determine the **static input-output characteristic** of the LED–sensor system:

1. PWM duty cycle varied automatically  
2. Light intensity measured for each PWM value  
3. Data transmitted via UART  
4. Results exported as CSV  
5. Characteristic plotted in external software  

This demonstrates interaction between actuator (LED) and sensor in an embedded feedback system. :contentReference[oaicite:7]{index=7}

---

## Learning Outcomes

The project demonstrates practical skills in:

- I²C communication implementation  
- Embedded sensor interfacing  
- PWM signal generation  
- UART data transmission  
- Embedded control system design  
- Laboratory measurement techniques :contentReference[oaicite:8]{index=8}

---

