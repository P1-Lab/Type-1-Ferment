# Control Logic

## System Model

The appliance operates as a multi-zone closed-loop control system with independent PID regulation per chamber.

---

## Control Loops

Each chamber maintains:

- Temperature PID loop
- Humidity PID loop
- Airflow regulation loop

---

## Operational Phases

### Ramp Phase
- Gradual temperature and humidity transition
- Used for fermentation initiation

### Hold Phase
- Stable environmental conditions
- Used for primary fermentation progression

### Vent Phase
- Controlled gas exchange cycles
- Removes excess CO₂ or volatile buildup

---

## Safety Control Logic

- Over-temperature cutoff
- Humidity saturation prevention
- Sensor drift detection and fallback defaults
- Emergency shutdown on critical failure states

---

## Data Logging

- Continuous environmental parameter logging
- Batch export in CSV format
- Timestamped fermentation state tracking
