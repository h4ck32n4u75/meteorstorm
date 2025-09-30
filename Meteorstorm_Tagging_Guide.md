# METEORSTORM Target of Exploitation Tagging Guide

## Operational Purpose
This guide ensures accurate, mission-aligned identification and tagging of the **Target of Exploitation (ToE)** in threat intelligence reporting using the METEORSTORM taxonomy. All ToE tags must reflect concrete adversary interest in a specific environment, capability, or asset — no assumptions, no guesswork.

---

## Tagging Workflow: Operational Decomposition

**Objective:** Determine **what is being targeted for exploitation** and assign the most specific classification available from each of the first four METEORSTORM layers:

1. **Primary Capability Environment (PCE)** – What physical environment(s) are the *targeted platform elements* operating in?
2. **Segment (SEG)** – Which structural component or system grouping is being *directly affected or exploited*?
3. **Service (SVC)** – What operational function is being *disrupted, degraded, or targeted*?
4. **Asset (AST)** – What technical element (hardware, firmware, software, data, or signal) is *specifically targeted or implicated* in the attack?

> Use positive identification only. Do not tag unless supported by technical indicators, adversary telemetry, or vetted modeling.

---

## Analytical Tagging Priorities (P1–P4)

After decomposing the ToE, assess the nature of the observed or modeled activity to determine the threat phase:

| Priority | Classification           | METEORSTORM Tag | Description                                                      |
|----------|--------------------------|-----------------|------------------------------------------------------------------|
| **P1**   | Indicator of Compromise   | `AN-IOC`        | Confirmed breach or malicious artifact tied to exploitation       |
| **P2**   | Indicator of Attack       | `AN-IOA`        | Targeting activity (e.g., scans, probes, staging) without confirmed compromise |
| **P3**   | Attack Path               | `AN-ATT`        | Modeled or observed path to effect exploitation across layers     |
| **P4**   | Threat                    | `AN-THR`        | Generalized or strategic threat capability or actor with interest in this ToE |

---

## Defensive Context Tags

If the intelligence indicates that a resilience measure or detection signature is available, assign:

- `AN-RES` — **Resilience Measure**: Capability that protects, mitigates, or recovers the platform  
- `AN-DET` — **Detection Signature**: Logic or telemetry pattern enabling threat detection  

---

## METEORSTORM Taxonomy Reference

### Primary Capability Environment (PCE)

| Tag    | Element      | Description                                                  |
|--------|--------------|--------------------------------------------------------------|
| PCE-TE | Terrestrial  | Surface-based operational zones on planetary bodies           |
| PCE-AQ | Aquatic      | Water-based operational zones, including Earth's maritime domains |
| PCE-AE | Aerial       | Atmospheric zones spanning low, high, and near-space regions  |
| PCE-OR | Orbital      | Operational zones within planetary or satellite orbits        |
| PCE-DS | Deep Space   | Operational zones beyond planetary orbital regimes            |

### Segment (SEG)

| Tag    | Element       | Description                                                  |
|--------|---------------|--------------------------------------------------------------|
| SEG-LA | Launch        | Surface-based infrastructure for launch ops                  |
| SEG-LI | Link          | Assets enabling signal transport (e.g., RF, FSO, relay)       |
| SEG-GR | Ground        | Terrestrial systems supporting control functions             |
| SEG-US | User          | End-user terminal or receiving equipment                     |
| SEG-AQ | Aquatic       | Maritime-based operations or service platforms               |
| SEG-LO | Low Altitude  | Lower-atmosphere air-based assets (e.g., drones)              |
| SEG-HI | High Altitude | Platforms above lower atmosphere but below orbital            |
| SEG-NE | Near Space    | Suborbital assets between upper atmosphere and orbit          |
| SEG-SP | Space         | Orbital satellites or on-platform payloads                   |
| SEG-DE | Deep Space    | Platforms operating beyond Earth orbit                       |

### Service (SVC)

| Tag    | Element       | Description                                     |
|--------|---------------|-------------------------------------------------|
| SVC-CP | Control Plane | Command and control services (TT&C, bus management) |
| SVC-DP | Data Plane    | Mission output services (e.g., payload transmission) |
| SVC-HY | Hybrid        | Integrated control and data delivery services   |

### Asset (AST)

| Tag    | Element   | Description                                  |
|--------|-----------|----------------------------------------------|
| AST-HW | Hardware  | Physical components (e.g., radios, sensors)   |
| AST-FW | Firmware  | Embedded software managing hardware           |
| AST-SW | Software  | Applications, protocols, or control logic     |
| AST-DA | Data      | Information generated or used by the platform |
| AST-SI | Signal    | Radio frequency or optical communication channels |
| AST-HY | Hybrid    | Asset blending multiple technical types       |

### Analytic (AN)

| Tag    | Element              | Description                          |
|--------|----------------------|--------------------------------------|
| AN-IOC | Indicator of Compromise | Confirmed evidence of compromise     |
| AN-IOA | Indicator of Attack     | Evidence of adversary staging or targeting |
| AN-ATT | Attack Path             | Pathway or chain of exploitation      |
| AN-THR | Threat                  | Known or modeled threat actor/capability |
| AN-DET | Detection Signature     | Known method of detection             |
| AN-RES | Resilience Measure      | Validated protection or recovery method |

---

## Final Guidance for Operators

- **Tag what the adversary is targeting**, not what you suspect.  
- **Use multiple tags** only when clearly supported (e.g., `PCE-OR`, `SEG-SP`, `SVC-DP`, `AST-SW`, `AN-IOA`).  
- **Omit layers without evidence.** No signal path described? Don’t assign `SEG-LI`.  
- **Prioritize clarity over coverage.** Precision wins over breadth.  

> This guide is mission critical. Review tags with your fusion cell during after-action reviews to ensure tagging aligns with real-world threat behaviors.
