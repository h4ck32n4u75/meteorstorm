# METEORSTORM Target of Exploitation Tagging Guide

This repository contains the official **Target of Exploitation (ToE) Tagging Guide** for the [METEORSTORM™](https://start.ethicallyhacking.space) threat taxonomy. It enables structured, threat-informed decomposition of observed or modeled adversary activity across five analytical layers:

- **Primary Capability Environment (PCE)**  
- **Segment (SEG)**  
- **Service (SVC)**  
- **Asset (AST)**  
- **Analytic (AN)**

## 🎯 Purpose

To support **mission-driven threat intelligence** and **operational security teams** in accurately identifying and tagging exploited elements within space, cyber, and multi-domain platforms. This guide ensures:

- Precision in attributing targeting activity  
- Consistency in analytical tagging across layers  
- Decision support for incident triage, correlation, and detection engineering  

## 📦 Contents

- `Meteorstorm_Tagging_Guide.md`: Analyst-facing guide for decomposing threat reports   

## ⚖️ Usage Policy

Tags must reflect *positively identified* targeting behavior. Do **not** use speculative tagging. This guide supports **analyst discipline** and **defensive coordination** during triage, reporting, and red/blue operations.

## 🛠 Integration

The `machinetag.json` file can be installed as a custom taxonomy in MISP to enforce this tagging structure during ingestion, enrichment, or post-processing.
