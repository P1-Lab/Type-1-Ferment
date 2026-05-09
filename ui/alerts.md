### ui/alerts.md

This document defines system alerts, escalation logic, and operator response requirements for the Auream OS interface.

---

#### 1. Alert Severity Levels

The system classifies events into four distinct tiers based on impact and required response.

| Level | Classification | System Behavior | UI Manifestation |
| --- | --- | --- | --- |
| **1** | **Advisory** | Minor deviation detected; no process interruption. | Discrete status icon; persistent log entry. |
| **2** | **Warning** | Sustained deviation; automatic correction cycles engaged. | Amber notification banner; requires operator acknowledgement. |
| **3** | **Critical** | Approaching safety thresholds; partial subsystem shutdown may occur. | Flashing red alert; audible signal; diagnostic telemetry prioritized. |
| **4** | **Fault / Emergency** | Immediate transition to **Safe State**; full process suspension. | Full-screen lockout; diagnostic code display; manual reset required. |

---

#### 2. Fault Categories

Specific diagnostic triggers and automated mitigation protocols.

* **Thermal Fault**
* **Trigger:** Internal temperature exceeds the defined safety envelope for the active profile.
* **Actions:** Immediate heater shutdown, airflow escalation to maximum, and system lock if the deviation persists $>300$ seconds.


* **Humidity Fault**
* **Trigger:** Relative Humidity (RH) deviation $>5\%$ for a duration $>10$ minutes.
* **Actions:** Halt ultrasonic vapor system, activate dehumidification/purge cycle.


* **Airflow Fault**
* **Trigger:** Fan RPM failure or intake/exhaust obstruction detected via pressure differential sensors.
* **Actions:** Crossflow array shutdown; process pause to prevent anaerobic/aerobic imbalance.


* **Sterilization Conflict**
* **Trigger:** Attempted initiation of UVC/Steam cycle while a fermentation profile is active.
* **Actions:** Command rejected; logic-gate interlock remains active; violation event logged to batch history.



---

#### 3. Safe State Protocol

In the event of a Level 4 Fault, the system executes the following sequence to protect hardware and substrate integrity:

1. **Process Suspension:** All active timers and fermentation cycles are paused.
2. **Thermal Cutoff:** Power is cut to all heating elements.
3. **Atmospheric Purge:** Fan arrays are set to a high-volume purge mode to exhaust heat or excess moisture.
4. **Interface Lock:** The HMI is locked to the **Diagnostics & Troubleshooting** screen, preventing further input until a physical reset or technician-level override is performed.
5. **Telemetry Freeze:** The final environmental state is captured and appended to the batch CSV for forensic audit.
