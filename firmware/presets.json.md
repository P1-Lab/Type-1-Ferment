
---

# firmware/

This section defines the embedded control logic, environmental operating profiles, and automation behavior for the dual-chamber fermentation appliance under the Auream OS control system.

---

## 1. Environmental Profiles (`presets.json`)

The system defines deterministic environmental profiles used to standardize fermentation conditions across repeatable production cycles.

Each profile specifies temperature, humidity, duration, airflow, and safety constraints.

---

### 1.1 Mycelial Pre-Treatment Profile

**Purpose:** Solid-state biological pre-processing of plant and organic substrates via fungal colonization.

* Duration: 14–30 days
* Temperature: 24–28°C
* Relative Humidity: 85–90% RH
* Airflow: low-velocity aerobic circulation (continuous crossflow)

**Functional Objective:**

* enzymatic breakdown of fibrous plant matter
* reduction of bitterness compounds
* structural pre-conditioning of biomass substrates

---

### 1.2 Koji Fermentation Profile

**Purpose:** Controlled Aspergillus oryzae fermentation for enzymatic saccharification and umami development.

* Duration: 24–72 hours
* Temperature: 28–35°C
* Critical Safety Threshold: >35°C triggers thermal mitigation response
* Relative Humidity: 75–80% RH
* Airflow: continuous aerobic crossflow ventilation

**Functional Objective:**

* enzymatic starch conversion
* protein breakdown into amino acid precursors
* controlled mycelial propagation under oxygenated conditions

---

### 1.3 Long Fermentation (Thermal Enzymatic) Profile

**Purpose:** Extended enzymatic transformation under elevated thermal conditions.

* Duration: 30–60 days
* Temperature: 58–62°C
* Relative Humidity: 70–80% RH

**Functional Objective:**

* accelerated enzymatic reaction kinetics
* controlled protein and lipid modification
* stabilization of long-duration ferment substrates

---

### 1.4 High-Fat Fermentation Profile

**Purpose:** Long-duration fermentation of lipid-rich substrates with controlled oxidative mitigation.

* Duration: 30–60 days
* Temperature: 60–65°C
* Relative Humidity: 75–85% RH
* Atmospheric Control: periodic gas exchange cycles (CO₂/O₂ venting)

**Functional Objective:**

* prevention of anaerobic spoilage pathways
* controlled lipid oxidation management
* stabilization of high-fat biochemical substrates

