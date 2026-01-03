# Part 1 — Executive Explanation  
## Sensitivity Analysis of Edge AI Telemetry Triage

---

## Purpose of This Analysis

This section explains **how and why the system behaves** when key detection parameters are adjusted.  
The goal is to demonstrate **predictable trade-offs**, not to claim a single “perfect” configuration.

---

## Key Concepts (Plain Language)

**Telemetry**  
Continuous health data from a satellite (battery voltage, temperature, attitude error).

**Time To Awareness (TTA)**  
The time between a real anomaly occurring and operators becoming aware of it.  
Lower TTA means faster reaction.

**False Positives**  
Alerts triggered when no real issue exists.  
Too many false positives reduce trust and overload operators.

**Bandwidth Savings**  
The percentage of telemetry data that does *not* need to be transmitted to the ground because it was handled onboard.

**Rolling Window**  
The recent time window used to define “normal” behavior.
- Short window → fast but sensitive  
- Long window → stable but slower

**Z-Threshold**  
How far a value must deviate from normal before being flagged.
- Low Z → very sensitive  
- High Z → conservative

---

## Chart 1 — False Positives Heatmap  
**False Positives per Hour vs Detection Sensitivity**

![False Positives Heatmap](../evaluation/results/heatmap_false_positives.png)

### Explanation

False positives are highest when:
- **Z-threshold is low** (system is very sensitive)
- **Rolling window is long (120s)**

A long rolling window adapts slowly, so small normal fluctuations appear more significant.  
With a low Z-threshold, these harmless deviations are frequently flagged.

This behavior is **expected and correct**, showing that sensitivity and noise are directly linked.

---

## Chart 2 — Bandwidth Savings Heatmap  
**Bandwidth Savings vs Detection Sensitivity**

![Bandwidth Savings Heatmap](../evaluation/results/heatmap_bandwidth_savings.png)

### Explanation

Bandwidth savings remain high across most configurations (≈95–98%).

At very long rolling windows:
- Detection is slower
- When an anomaly is confirmed, **more context data is transmitted**
- This slightly reduces savings percentage

This represents a realistic trade-off between responsiveness and transmission efficiency.

---

## Why This Matters

These results demonstrate that:
- The system is **tunable, not fragile**
- Trade-offs are transparent and controllable
- Significant operational gains are possible without full autonomy

This PoC proves feasibility and operational discipline, not exaggerated claims.
