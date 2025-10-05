# IoT-Based Wireless Charging Station for Electric Vehicles (EVs)

## Project Overview

This project is a prototype of a smart, IoT-enabled wireless charging station for Electric Vehicles (EVs). The system uses the principle of inductive power transfer to charge a vehicle without any physical connection. The core of the system is an STM32 microcontroller, which manages vehicle detection, power transmission, and status monitoring, providing a seamless and automated charging experience.

This repository contains the firmware developed for the STM32 microcontroller which acts as the central control unit for the charging station.



## Key Features

- **Automated Vehicle Detection:** An IR sensor automatically detects the presence of an EV in the charging bay.
- **Microcontroller-Based Control:** The entire process is orchestrated by an STM32 microcontroller, ensuring reliable and efficient operation.
- **Real-Time Status Display:** A 16x2 LCD display provides instant feedback on the charging status (e.g., "Idle", "Vehicle Detected", "Charging").
- **Wireless Power Transfer:** Utilizes inductive coupling to transmit power from the charging pad to the vehicle's receiver coil.
- **IoT-Ready:** The system is designed to transmit real-time data like voltage and current for remote monitoring (feature in development).

## My Role: Embedded Software & Control Systems

As the lead on the embedded systems and firmware development, my primary responsibilities were centered around programming the STM32 microcontroller and integrating the hardware components.

### 1. Firmware Architecture & Development
- Developed the complete control logic in C/C++ for the STM32 board.
- Wrote clean, modular, and well-documented code to manage the system's states: idle, vehicle detection, and active charging.
- Implemented the high-frequency signal generation required to drive the MOSFET for the transmitter coil.

### 2. Peripheral Integration & Drivers
- Interfaced the IR proximity sensor to detect the arrival and departure of the vehicle. My code was responsible for reading the sensor's digital signal and triggering the appropriate system response.
- Programmed the control logic for the relay module, which safely switches the main power to the transmitter circuit only when a vehicle is present.
- Wrote the driver and API to control the 16x2 LCD, allowing for dynamic display of system status messages.

### 3. System Logic & State Management
- Designed and implemented the core state machine that governs the charging process.
- Ensured smooth transitions between states based on real-time sensor input, providing a fully automated user experience.

## System Workflow

1.  **Initialization:** The STM32 microcontroller initializes all peripherals, and the LCD displays "Status: Idle".
2.  **Vehicle Detection:** The IR sensor detects a vehicle and sends a signal to the STM32.
3.  **Power Activation:** The STM32 firmware processes the signal, updates the LCD to "Vehicle Detected," and activates a relay.
4.  **Charging:** The relay connects the transmitter circuit to the power supply. The STM32 then generates a high-frequency signal to the MOSFET, creating an oscillating magnetic field in the primary coil to begin wireless power transfer.
5.  **Completion/Departure:** When the vehicle leaves, the IR sensor signals the STM32, which deactivates the relay, stops the power transmission, and returns the system to an "Idle" state.

## Hardware Components

- **Microcontroller:** STM32 Board
- **Sensor:** IR Proximity Sensor
- **Display:** 16x2 LCD
- **Switching:** 5V Relay Module
- **Power Electronics:** MOSFET, 7805 Voltage Regulators
- **Wireless Transfer:** Custom-wound Transmitter & Receiver Coils

## Project Status & Results

The control system, managed by the STM32 firmware, performed flawlessly. The IR sensor, relay logic, and LCD status updates all worked exactly as designed, successfully demonstrating a robust embedded control system.

The primary limitation was in the efficiency of the physical wireless power transfer due to the distance between the coils and the gauge of the wire used. While the charging was not powerful, the project was a successful proof-of-concept for the automated control and monitoring logic, which was the focus of my contribution.
