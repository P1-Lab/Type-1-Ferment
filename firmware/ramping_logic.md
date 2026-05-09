---

## 2. Ramping Logic (`ramping_logic.md`)

The system employs parametric ramp control to transition between environmental states without introducing thermal or humidity shock to biological substrates.

---

### 2.1 Thermal Ramp Control

* Temperature transitions are executed as linear or curved setpoint ramps
* Each chamber operates an independent PID control loop
* Control tolerances:

  * Chamber A: ±0.1°C
  * Chamber B: ±0.2°C

Ramp execution is designed to:

* prevent thermal stress to active cultures
* maintain enzymatic continuity during phase transitions

---

### 2.2 Humidity Regulation

* Humidity is governed via closed-loop proportional control of ultrasonic vaporization systems
* Target tolerance: ±2% RH

Failure mitigation logic:

* If RH exceeds setpoint by >5% for >10 minutes:

  * dehumidification subsystem engages automatically
  * vapor generation is suspended until stabilization

---

### 2.3 Gas Exchange Cycles (High-Fat Profile)

* Automated CO₂/O₂ valve cycling:

  * interval: 6–12 hours
  * vent duration: 10–30 minutes

Purpose:

* removal of accumulated metabolic gases
* mitigation of lipid oxidation risk in high-fat substrates
* maintenance of controlled atmospheric equilibrium

---

### 2.4 Safety Overrides

The system enforces non-bypassable safety constraints:

#### Thermal Protection

* Substrate temperature monitoring is continuous
* If temperature exceeds 35°C (Koji profile threshold):

  * heating elements are disabled
  * airflow is increased
  * alert state is triggered

#### Sanitation Interlock

* UVC sterilization and steam sanitation cycles are mutually exclusive with active fermentation states
* All fermentation processes must be in idle or paused state before sterilization execution

