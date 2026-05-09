# System Architecture

## Overview

The system consists of two independently controlled fermentation chambers governed by a central embedded controller.

---

## Subsystems

### Chamber A (Solid-State Fermentation Zone)
- Aerobic fermentation environment
- Controlled temperature and humidity
- Forced low-velocity airflow system
- HEPA and activated carbon filtration

### Chamber B (Extended Fermentation Zone)
- Long-duration fermentation environment
- Programmable thermal cycling
- Controlled gas exchange system

---

## Airflow System

### Intake Path
Ambient air → HEPA filtration → carbon filtration → Chamber A

### Exhaust Path
Chamber B → gas regulation valves → exhaust filtration system

---

## Thermal Zoning

- Chambers thermally isolated via 80 mm polyurethane insulation
- Independent heating elements per chamber

---

## Humidity System

- Ultrasonic humidification system
- Feedback-controlled via RH sensors
- Optional filtered water input system

---

## Control System

- Central embedded controller
- Independent PID loops per chamber
- Sensor-driven closed-loop regulation of:
  - temperature
  - humidity
  - airflow
  - gas composition
