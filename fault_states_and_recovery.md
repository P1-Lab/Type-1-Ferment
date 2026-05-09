# Fault States and Recovery

## Sensor Failure

### Condition
- Temperature or humidity sensor invalid or non-responsive

### Response
- Switch to safe default PID values
- Trigger maintenance alert

---

## Over-Temperature Condition

### Condition
- Chamber exceeds defined thermal threshold

### Response
- Immediate heating shutdown
- Increased airflow activation
- Emergency cooling cycle

---

## Humidity Oversaturation

### Condition
- RH exceeds upper limit for more than defined interval

### Response
- Deactivate humidifier
- Increase exhaust ventilation

---

## Gas Flow Blockage

### Condition
- CO₂/O₂ exchange system restricted

### Response
- Ventilation override mode
- System lock until cleared

---

## Power Loss Recovery

### Condition
- Unexpected system shutdown

### Response
- Resume last known safe state after reboot
- Validate sensor integrity before restart
