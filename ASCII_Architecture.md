# System Overview (ASCII Architecture)

## Dual-Chamber Controlled Fermentation Appliance

This document provides a high-level structural and functional overview of the system architecture, including airflow, thermal zoning, and control hierarchy.

---

# 1. SYSTEM BLOCK ARCHITECTURE
                ┌──────────────────────────────┐
                │      CENTRAL CONTROLLER      │
                │   (Embedded Control Unit)    │
                └─────────────┬────────────────┘
                              │
    ┌─────────────────────────┼─────────────────────────┐
    │                         │                         │
    ▼                         ▼                         ▼
┌───────────────┐ ┌──────────────────┐ ┌──────────────────┐
│ SENSOR ARRAY │ │ CONTROL SYSTEM │ │ USER INTERFACE │
│ │ │ │ │ │
│ Temp Sensors │ │ PID Loops │ │ Touchscreen UI │
│ Humidity │ │ Phase Control │ │ Data Export │
│ Gas Sensors │ │ Safety Logic │ │ Parameter Input │
└───────┬───────┘ └────────┬─────────┘ └──────────────────┘
│ │
└──────────────┬────────┘
│
┌──────────────▼──────────────┐
│ DUAL CHAMBERS │
└──────────────┬──────────────┘
│
┌──────────────┴──────────────┐
▼ ▼
┌────────────────┐ ┌────────────────┐
│ CHAMBER A │ │ CHAMBER B │
│ (Solid-State) │ │ (Extended Fer.) │
└────────────────┘ └────────────────┘

---

# 2. AIRFLOW SYSTEM

        AMBIENT AIR
             │
             ▼
    ┌──────────────────┐
    │   HEPA FILTER    │
    └──────────────────┘
             │
             ▼
    ┌──────────────────┐
    │ CARBON FILTER    │
    └──────────────────┘
             │
             ▼
    ┌──────────────────────────┐
    │      CHAMBER A           │
    │  (Crossflow Air System)  │
    └─────────────┬────────────┘
                  │
                  ▼
        ┌──────────────────────┐
        │   INTER-CHAMBER      │
        │   AIR MANAGEMENT     │
        └─────────┬────────────┘
                  │
                  ▼
    ┌──────────────────────────┐
    │      CHAMBER B           │
    │ (Gas-Controlled Zone)    │
    └─────────────┬────────────┘
                  │
                  ▼
    ┌──────────────────┐
    │  EXHAUST FILTER  │
    └──────────────────┘
                  │
                  ▼
            EXTERNAL OUT



---

# 3. THERMAL ZONING MODEL


┌──────────────────────────────────────────────┐
│ OUTER CHASSIS │
│ (Insulated Steel Enclosure) │
│ │
│ ┌──────────────────────────────┐ │
│ │ CHAMBER A │ │
│ │ 20–36°C CONTROL RANGE │ │
│ │ High humidity 70–95% RH │ │
│ └──────────────────────────────┘ │
│ │
│ ┌──────────────────────────────┐ │
│ │ CHAMBER B │ │
│ │ 40–75°C CONTROL RANGE │ │
│ │ Controlled gas exchange │ │
│ └──────────────────────────────┘ │
│ │
│ 80mm Polyurethane Thermal Barrier Layer │
└──────────────────────────────────────────────┘


---

# 4. CONTROL LOOP ARCHITECTURE

    ┌──────────────────────────┐
    │   CENTRAL CONTROLLER     │
    └────────────┬─────────────┘
                 │
 ┌───────────────┼────────────────┐
 │               │                │
 ▼               ▼                ▼

┌───────────┐ ┌───────────┐ ┌──────────────┐
│ TEMP PID │ │ HUMID PID │ │ GAS CONTROL │
└─────┬─────┘ └─────┬─────┘ └──────┬───────┘
│ │ │
▼ ▼ ▼

[Heaters] [Humidifier] [CO₂/O₂ Valves]
[Cooling] [Water Input] [Vent System]
[Fans]


---

# 5. CHAMBER FUNCTIONAL FLOW

## CHAMBER A (Aerobic Fermentation)

INPUT SUBSTRATE
│
▼
[HEATED HUMIDIFIED ENVIRONMENT]
│
▼
[KOJI / MYCELIAL GROWTH PHASE]
│
▼
[ENZYME DEVELOPMENT + STRUCTURAL BREAKDOWN]
│
▼
OUTPUT TO STAGING OR DRYING


---

## CHAMBER B (Extended Fermentation)

INPUT SUBSTRATE
│
▼
[THERMAL ENZYME REACTION ZONE]
│
▼
[CONTROLLED GAS EXCHANGE LOOP]
│
▼
[LONG-DURATION BIOCHEMICAL TRANSFORMATION]
│
▼
STABILIZED OUTPUT MATERIAL


---

# 6. SYSTEM STATE MACHINE (HIGH LEVEL)


[IDLE]
│
▼
[RAMP PHASE]
│
▼
[ACTIVE FERMENTATION]
│
├──> [KOJI MODE]
├──> [MYCELIAL MODE]
├──> [LAB MODE]
└──> [HIGH-FAT MODE]
│
▼
[HOLD / STABILIZATION]
│
▼
[VENT / RESET CYCLE]
│
▼
[STERILIZATION MODE]
│
▼
[IDLE]


---

# 7. SYSTEM SUMMARY

The appliance operates as a dual-zone, closed-loop fermentation system with:

- independent thermal chambers  
- real-time environmental feedback loops  
- gas composition modulation  
- sterilization and sanitation subsystems  
- state-based operational modes  

It is designed for reproducible, programmable fermentation under tightly controlled environmental parameters.




