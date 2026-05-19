# Smart IoT Based Irrigation System using LPC2148 and ESP01

## Project Overview

This project is a **Smart IoT Based Irrigation System** developed using the **LPC2148 ARM7 microcontroller**. The system monitors environmental and soil conditions using a **DHT11 temperature and humidity sensor** and a **soil moisture sensor**. Based on the sensor readings and selected crop conditions, the system automatically controls a **relay/pump** for irrigation.

The measured temperature and humidity values are also sent to the **ThingSpeak Cloud** using an **ESP01 Wi-Fi module** through UART communication.

This project is useful for smart agriculture applications where irrigation can be automated based on real-time temperature, humidity, soil moisture, and crop requirements.

---

## Objective

The main objective of this project is to design and implement an embedded IoT-based irrigation system that can:

- Monitor temperature using DHT11 sensor
- Monitor humidity using DHT11 sensor
- Detect soil dry/wet condition using soil moisture sensor
- Select crop type using keypad
- Display sensor values and system status on LCD
- Automatically control relay/pump based on conditions
- Send temperature and humidity values to ThingSpeak cloud
- Reduce manual irrigation effort
- Improve water usage efficiency in agriculture

---

## Features

- Real-time temperature monitoring
- Real-time humidity monitoring
- Soil moisture dry/wet detection
- Automatic pump/relay control
- Crop-based irrigation decision
- Keypad-based crop selection
- LCD display for real-time status
- ESP01 Wi-Fi communication
- ThingSpeak cloud data update
- UART0 based communication
- External interrupt support
- Modular Embedded C programming
- Low-cost smart agriculture solution

---

## Hardware Components Required

| S.No | Component | Purpose |
|---|---|---|
| 1 | LPC2148 ARM7 Development Board | Main controller |
| 2 | DHT11 Sensor | Temperature and humidity measurement |
| 3 | Soil Moisture Sensor | Soil dry/wet detection |
| 4 | ESP01 Wi-Fi Module | Sending data to ThingSpeak cloud |
| 5 | 16x2 LCD | Displaying sensor values and status |
| 6 | 4x4 Keypad | Crop selection and user input |
| 7 | Relay Module | Pump or bulb control |
| 8 | Water Pump / Bulb | Output load |
| 9 | 3.3V Regulator | ESP01 and LPC2148 compatible supply |
| 10 | 5V Supply | LCD and relay module |
| 11 | Jumper Wires | Hardware connections |
| 12 | Breadboard / PCB | Circuit assembly |

---

## Software Requirements

| Software | Purpose |
|---|---|
| Keil uVision4 | Embedded C code development |
| Flash Magic | Flashing HEX file into LPC2148 |
| Proteus | Circuit simulation |
| ThingSpeak | Cloud data visualization |
| Embedded C | Programming language |
| Serial Terminal | ESP01 AT command testing |

---

## Microcontroller Used

## LPC2148 ARM7 Microcontroller

The LPC2148 is an ARM7TDMI-S based microcontroller. It is suitable for embedded applications because it supports GPIO, UART, timers, interrupts, ADC, and other peripherals.

In this project, LPC2148 is used for:

- Reading DHT11 sensor data
- Reading soil moisture sensor digital output
- Scanning keypad input
- Displaying data on LCD
- Controlling relay/pump
- Communicating with ESP01 using UART0
- Handling external interrupt input

---

## Pin Configuration

| Module | Signal | LPC2148 Pin |
|---|---|---|
| ESP01 RX | UART0 TXD0 | P0.0 |
| ESP01 TX | UART0 RXD0 | P0.1 |
| External Interrupt | EINT1 input | P0.3 |
| DHT11 Sensor | Data pin | P0.4 |
| Soil Moisture Sensor | Digital output | P0.5 |
| LCD Data Pins | D0 to D7 | P0.8 to P0.15 |
| LCD RS | Register Select | P0.16 |
| LCD EN | Enable | P0.17 |
| Relay Module | Relay input | P0.20 |
| Keypad Rows and Columns | 4x4 keypad | P1.16 to P1.23 |

---

## Circuit Connections

## DHT11 Sensor Connection

| DHT11 Pin | Connection |
|---|---|
| VCC | 3.3V / 5V |
| DATA | LPC2148 P0.4 |
| GND | GND |

A 4.7kΩ or 10kΩ pull-up resistor can be connected between DATA and VCC.

---

## Soil Moisture Sensor Connection

| Soil Sensor Pin | Connection |
|---|---|
| VCC | 3.3V / 5V |
| GND | GND |
| DO | LPC2148 P0.5 |
| AO | Not used |

In this project, the digital output pin is used.

Example logic:

```c
if(IO0PIN & (1 << 5))
{
    // Soil is dry
}
else
{
    // Soil is wet
}
