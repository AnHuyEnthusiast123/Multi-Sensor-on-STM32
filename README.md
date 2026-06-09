# STM32 Multi-Sensor Monitoring and Adaptive Brightness Control

> Bare-metal STM32F401RE project for environmental monitoring, sensor interfacing, and automatic brightness control using low-level peripheral programming.

---

## Overview

This project demonstrates the development of a real-time embedded monitoring system on the STM32F401RE microcontroller. The system integrates multiple peripherals and sensors to collect environmental data, display measurements on an LCD screen, and automatically adjust display brightness based on ambient light conditions.

The project was implemented using low-level embedded C programming with direct interaction between hardware peripherals and external devices through SPI, I2C, ADC, DMA, and PWM modules.

---

## Key Features

* Real-time temperature monitoring
* Real-time humidity monitoring
* Ambient light sensing
* LCD graphical display
* Automatic brightness control
* ADC Polling and DMA support
* SPI communication with LCD
* I2C communication with sensors
* PWM-based LED brightness adjustment
* Bare-metal STM32 peripheral programming

---

## Hardware Components

| Component    | Description                     |
| ------------ | ------------------------------- |
| STM32F401RE  | Main microcontroller            |
| SI7020       | Temperature and humidity sensor |
| Light Sensor | Ambient light measurement       |
| ST7735 LCD   | Sensor data visualization       |
| LED          | Brightness control output       |

---

## System Architecture

```text
                    +-------------------+
                    |   STM32F401RE     |
                    +---------+---------+
                              |
        +---------------------+----------------------+
        |                                            |
      I2C                                          ADC
        |                                            |
     SI7020                                    Light Sensor
        |
  Temperature / Humidity

        SPI
         |
    ST7735 LCD

        PWM
         |
    LED Brightness
```

---

## Software Architecture

### Sensor Layer

Responsible for acquiring environmental data.

* SI7020 temperature sensor
* SI7020 humidity sensor
* Ambient light sensor

### Peripheral Layer

Implements low-level drivers for:

* GPIO
* SPI
* I2C
* ADC
* DMA
* Timer/PWM
* SysTick

### Application Layer

Responsible for:

* Periodic sensor acquisition
* Data processing
* LCD updates
* Brightness control
* System scheduling

---

## Peripheral Implementation

### SPI Driver

Used to communicate with the ST7735 LCD display.

Features:

* LCD initialization
* Command transmission
* Data transmission
* Real-time value rendering

### I2C Driver

Used to communicate with the SI7020 sensor.

Features:

* Register read/write operations
* Temperature acquisition
* Humidity acquisition
* Error handling and bus control

### ADC Driver

Used to sample ambient light intensity.

Supported modes:

* Polling Mode
* DMA Mode

### DMA Driver

Provides efficient ADC data transfer without continuous CPU intervention.

Benefits:

* Reduced CPU overhead
* Improved sampling efficiency
* Continuous data acquisition

### PWM Driver

Used to control LED brightness.

Features:

* Timer-based PWM generation
* Adjustable duty cycle
* Smooth brightness transitions

---

## Automatic Brightness Control

The Automatic Brightness Control (ABC) module simulates the adaptive brightness feature commonly found in smartphones.

### Workflow

1. Read ambient light intensity through ADC.
2. Convert ADC value into brightness percentage.
3. Calculate PWM duty cycle.
4. Update LED brightness.
5. Refresh LCD display.

```text
Light Sensor
      |
      v
ADC Sampling
      |
      v
Brightness Mapping
      |
      v
PWM Generation
      |
      v
LED Brightness Adjustment
```
---

## Example Output

```text
Temperature : 29°C
Humidity    : 72%
Light Level : 1580

Brightness  : 68%
PWM Duty    : 68%
```

---

## Development Highlights

* Implemented low-level peripheral drivers without relying on high-level frameworks.
* Developed SPI-based LCD communication for real-time visualization.
* Built I2C communication routines for environmental sensors.
* Implemented ADC acquisition using both Polling and DMA modes.
* Designed PWM-based adaptive brightness control logic.
* Applied memory-efficient embedded C programming techniques.

---

## Build Environment

### Software

* STM32CubeIDE
* STM32 SDK
* Embedded C

### Target Platform

* STM32F401RE Nucleo Board

---

## Build and Flash

### Build Project

```bash
Project -> Build Project
```

### Flash to Target

```bash
Run -> Debug
```

or

```bash
Run -> Run As -> STM32 Cortex-M C/C++ Application
```

---

## Learning Outcomes

This project provided practical experience in:

* Embedded C programming
* Bare-metal firmware development
* STM32 peripheral configuration
* SPI and I2C communication protocols
* ADC and DMA operation
* PWM signal generation
* Sensor integration
* Real-time embedded system design

---

## Future Improvements

* FreeRTOS integration
* Sensor data logging
* MQTT connectivity
* Wi-Fi/Bluetooth communication
* Edge-AI inference on STM32
* Remote monitoring dashboard

---

## Author

**Tran An Huy**

Embedded Systems • IoT • Edge Computing • Distributed Systems
