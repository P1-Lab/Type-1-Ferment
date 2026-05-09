### ui/controls.md

This document defines all operator-adjustable inputs exposed through the HMI for the **Type 1: Ferment** appliance.

---

#### 1. Environmental Controls

Operators can fine-tune the internal environments of Chamber A and Chamber B within specific engineering envelopes.

* **Temperature Setpoints:**
* **Chamber A:** 20–36°C
* **Chamber B:** 40–75°C
* **Adjustment Granularity:** 0.1°C
* **Safety Note:** Hard safety overrides remain firmware-controlled to prevent substrate combustion or hardware damage.


* **Humidity Control:**
* **Range:** 60–95% RH (dependent on active mode).
* **Adjustment Granularity:** 1% RH.
* **Stabilization:** Auto-correct is enabled by default via PID feedback loops to maintain atmospheric consistency.


* **Airflow Control:**
* **Low (Mycelial):** Minimized velocity to prevent surface drying.
* **Medium (Koji):** Optimized for metabolic heat dissipation.
* **High (Sterilization Assist):** Maximum exchange for post-cycle venting.
* **Override Status:** Manual override is disabled during active fermentation cycles to ensure process integrity.



---

#### 2. Process Controls

Time-based and progression-based parameters governing the fermentation lifecycle.

* **Fermentation Duration:**
* Adjustable only within established safety and efficacy boundaries:
* **Mycelial Pre-Treatment:** 14–30 days.
* **Koji Fermentation:** 24–72 hours.
* **Long Ferment:** 30–60 days.




* **Ramp Profiles:**
* **Linear Ramp:** Uniform temperature/humidity progression.
* **Curved (Enzyme-Preserving):** Non-linear ramping designed to protect delicate enzymatic structures during initial activation.
* **Stepped Stabilization:** Industrial-grade mode utilizing distinct plateau phases for complex substrate transitions.



---

#### 3. Safety-Controlled Locks (Non-Adjustable)

To maintain structural integrity and food safety standards, the following parameters are firmware-locked and cannot be modified by the operator:

* **Thermal Cutoff Thresholds:** Hard-coded limits for heaters and electronics bays.
* **Gas Venting Frequency:** Minimum safety intervals for $CO_2/O_2$ exchange to prevent pressure buildup.
* **Sterilization Cycle Parameters:** Temperatures and durations required for 99.9% microbial reduction.
* **Component Timing:** HEPA filtration duty cycles and UVC activation sequences.
