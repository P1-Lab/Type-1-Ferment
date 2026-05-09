### ui/telemetry.md

This document defines the real-time data representation rules and streaming logic for the Auream OS HMI layer, ensuring high-fidelity monitoring for precision fermentation.

---

#### 1. Sensor Streams

The HMI prioritizes the following data points for real-time visualization:

* **Chamber A (Aerobic Zone):**
* **Temperature:** Precision readout in °C ($\pm0.1$ resolution).
* **Humidity:** Relative humidity (% RH).
* **Airflow Velocity:** Real-time horizontal crossflow speed (m/s).


* **Chamber B (Enzymatic Zone):**
* **Temperature:** Precision readout in °C ($\pm0.2$ resolution).
* **Humidity:** Relative humidity (% RH).
* **Gas Composition State:** Binary or phase indicator for $CO_{2}/O_{2}$ exchange cycles.



---

#### 2. Update & Polling Frequency

To balance processor overhead with precision requirements, the system utilizes tiered polling:

* **Standard Mode:** 1 Hz sensor refresh rate for the HMI display.
* **Critical Alerts:** 5 Hz override polling for any sensor exceeding Level 2 (Warning) thresholds.
* **Historical Logging:** 1-minute data aggregation for the non-volatile system memory and batch log.

---

#### 3. Visualization Logic

The UI adapts its visual language based on the current system state:

* **Normal Operation:**
* Stable numeric readouts with high-contrast typography.
* **Trend Indicators:** Visual glyphs (rising / falling / stable) based on a 5-minute rolling average.


* **Active Fermentation:**
* **Phase Indicator Bar:** A progress-tracking element showing the current stage:
* `Ramp` (Environmental climb)
* `Active` (Peak metabolic activity)
* `Stabilization` (Enzymatic hold)
* `Vent Cycle` (Gas exchange active)




* **Fault State:**
* **Freeze-Frame Snapshot:** The HMI retains the last valid sensor state prior to the fault for forensic analysis.
* **Fault Overlay:** High-priority diagnostic modal obscuring standard telemetry until the state is acknowledged.



---

#### 4. Data Export Layer

Telemetry is exposed for R&D audit via a local WiFi interface.

* **Format:** Standardized CSV export.
* **Included Metadata:**
* Full sensor history (Time-stamped at 1-minute intervals).
* Mode transitions (e.g., transition from `Koji` to `Sterilization`).
* Detailed alert logs (Severity levels 1–4).
* System state changes (Manual overrides or automated safety triggers).
