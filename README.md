# Accumulator Managment System (High Voltage Battery Managment System) 2025

Accumulator Managment System (High Voltage Battery Managment System)

## Overview
The AMS system consists of two main parts, the master and multiple slaves.
<p align="center">
  <img src="https://github.com/user-attachments/assets/a5bbf403-06de-40c9-b362-9b193c4f06d8">
</p>
The apparatus is responsible for the managment of the battery as a whole, determining it's states like: state of charge or unsafe state plausibility. It also supervises the turning on and off of the hv bus.

## Features
What is the purpose of the Accumulator Management System?

The Accumulator Management System (AMS), also known as the HV-BMS, is the brain that controls and monitors the entire high-voltage battery pack in an electric vehicle.
Its main responsibilities include:

1. Safety Monitoring

Monitoring cell/module voltages

Monitoring charge/discharge current

Monitoring cell, module, and coolant temperatures

Shutting down the system in case of faults such as: OV, UV, OC, OT, short circuit, or isolation fault

The AMS ensures that the battery pack never operates outside safe limits, preventing damage or fire hazards.

2. Cell Balancing

Supports active or passive balancing

Keeps all cells at equal SOC levels

Optimizes battery lifespan and available capacity

3. Estimation of Battery States

The AMS calculates several key parameters:

SOC (State of Charge) – remaining battery percentage

SOH (State of Health) – battery aging/health condition

SOP (State of Power) – maximum deliverable or receivable power

SOE (State of Energy) – remaining usable energy

4. High-Voltage System Safety Control

Controlling contactors

Managing the precharge process

Monitoring the HVIL (High Voltage Interlock Loop)

Managing the discharge resistor

Interacting with TSAL, IMD, and the shutdown circuit

5. Communication With Other ECUs

The AMS typically communicates with:

CAN bus

Inverter

Vehicle Control Unit (VCU)

Charger / Onboard Charger

Thermal Management ECU


## Master
The AMS Master is the center of the whole system it's responsible for most of the tasks: current measurement, high voltage relay control, slave control, high voltage measurement and communication with the car. 
<p align="center"> 
  <img src="https://github.com/user-attachments/assets/76ba6605-d5d6-49a4-94d3-47f30560dd39">
</p>

### Software
The AMS system havely relies on RTOS (Real Time Operating System) for seperating and managing different tasks. The system is divided mainly into three parts:
- main task - responsible for control over the whole system,
- subsidiary tasks - for off handling time consuming calculations or interfacing,
- communication tasks - for handling communication with external systems like CAN communication with the car or isoSPI for communication with the slaves.

### Hardware 
The AMS is powered by STM32G484xx, a powerful, new gen MCU capable of handling varius communication interfaces and tasks. On board there are also three 24bit ADC ICs responsible for taking precise measurments of flowing current and voltage present on HV bus. For interfacing with other components the AMS uses M80 and M300 series Harwin connectors which offer high reliability. The board also features other logic components all on a custom 4 layer board.

<p align="center"> 
  <img src="https://github.com/user-attachments/assets/a7a89a94-febb-4723-b750-979644e198c7">
</p>
