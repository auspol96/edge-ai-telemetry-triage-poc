# Edge AI Telemetry Triage PoC

Simulation-validated proof of concept demonstrating onboard-style telemetry anomaly triage to reduce response time and downlink bandwidth.

## What this is
This repository contains a lightweight, conservative edge intelligence pipeline that detects, prioritizes, and triages satellite telemetry anomalies **before downlink**, validated using realistic simulation.

The goal is to demonstrate **operational value**, not flight readiness.

## Why it matters
- Ground-only monitoring delays anomaly awareness
- Continuous downlink wastes scarce bandwidth
- These problems scale poorly with constellation size

This PoC shows that **onboard triage alone** can:
- Reduce time-to-action by ~10–20 minutes
- Reduce downlinked telemetry volume by ~98%
- Preserve context for high-confidence anomalies

## What’s included
- Telemetry simulator with controlled anomaly injection
- Lightweight anomaly detection (rolling statistics + spike override)
- Event aggregation and severity-based decision logic
- Time-to-action and bandwidth impact evaluation

## Results (PoC)
- ⏱ Faster anomaly awareness vs ground-only baseline
- 📡 ~98% reduction in telemetry downlink volume
- 🧠 Conservative detection to minimize false positives

## Repository structure
/simulator Telemetry generation and anomaly injection
/pipeline Edge-style detection and triage logic
/evaluation Time-to-action and bandwidth analysis
/outputs Generated logs, decisions, and summaries
/whitepaper Technical PoC note (PDF)

## Important notes
- Simulation-only (no flight hardware)
- No autonomous control actions
- No UI or operational integration

## Learn more
- 📄 Technical details: `/whitepaper/Edge_AI_Telemetry_Triage_PoC_Whitepaper.pdf`
- 📘 Investor overview: `INVESTOR_README.md`
