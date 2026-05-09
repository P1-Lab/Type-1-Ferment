### ui/state_model.md

This document defines the operational screens of the touchscreen HMI as direct representations of system state machine modes for Auream OS.

---

#### 1. Primary Navigation States

The interface is state-driven. Only one primary system mode is active at any time.

```text
[BOOT]
  ↓
[IDLE / READY]
  ↓
[SELECT MODE]
  ↓
[ACTIVE OPERATION]
  ↓
[HOLD / MONITOR]
  ↓
[STERILIZATION]
  ↓
[FAULT / SAFE STATE]

```

---

#### 2. Mode-to-Screen Mapping

| System Mode | Functional Description | UI Display Requirements |
| --- | --- | --- |
| **IDLE / READY** | System powered and stable. | Chamber status (A/B), last run summary, filter health (HEPA/Charcoal), readiness indicator. |
| **SELECT MODE** | Profile selection interface. | Selection tiles for: Mycelial Pre-Treatment, Koji Fermentation, Long Ferment, High-Fat Fermentation. |
| **ACTIVE OPERATION** | Real-time environmental visualization. | Per-chamber temperature/humidity, airflow status, gas exchange cycles, and cycle phase progress timeline. |
| **HOLD / MONITOR** | Stabilized maintenance mode. | Real-time deviation tracking from setpoints; low-power UI state. |
| **STERILIZATION** | UVC + Steam cycle active. | Safety lock icon, active countdown timer, and interlock status. UI is locked to prevent accidental exposure. |
| **FAULT / SAFE STATE** | Critical override state. | Fault classification, affected subsystem identification, and required operator action. All processes suspended. |

---

#### 3. Control Logic Integration

* **Mode Transitions:** Transitions between `SELECT MODE` and `ACTIVE OPERATION` trigger the respective firmware PID tuning and sensor polling intervals.
* **Emergency Interrupt:** A persistent software-level "Global Stop" is accessible across all screens except during `BOOT`.
* **Data Logging:** While in `ACTIVE OPERATION` or `HOLD`, the system streams telemetry to the CSV batch log for export via WiFi.
