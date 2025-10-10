# METEORSTORM Threat Intelligence Tagging Guide

**Multiple Environment Threat Evaluation of Resources Space Threats and Operational Risk to Missions**

---

## Audience

Watch floor analysts, duty officers, fusion cell leads, ISAC/ISAO participants, space mission cyber operators

## Purpose

Provide a structured reference and operational guide to understanding, fusing, and sharing threat intelligence using METEORSTORM and MISP taxonomies.

METEORSTORM was designed with a critical first step: **align the community with a future-proof decomposition taxonomy** that could be used to "encapsulate" the "platform" context before, during, and after intelligence sharing. The key emphasis on "future proof" means the framework is specifically capable of encapsulating a diverse range of platform elements including:

- Legacy Space
- New Space
- Non-Terrestrial Networks (DTD and others)
- Deep Space
- NB IoT
- Subsea Cable Dependencies
- Autonomous Aerial Platforms
- Autonomous Aquatic Platforms

This future-oriented design ensures that as the threat landscape evolves and new platform types emerge, the taxonomy remains relevant and applicable across all domains.

## Prerequisites

This guide is intended for **operational use** in live watch center and fusion cell environments as well as community member environments for machine-to-machine sharing. It assumes:

- You have **MISP** (or another Threat Intelligence Platform) installed and operational
- The **METEORSTORM taxonomy** is imported and activated in your platform
- You have appropriate permissions to tag, enrich, and share intelligence objects
- TLP/PAP controls are configured and enforced in your sharing community

These prerequisites ensure that the tagging workflows and examples in this guide can be applied directly in real-world operational settings.

---

## 1. Background: Threat Intelligence

Threat intelligence (TI) refers to evidence-based knowledge about existing or emerging threats, including indicators, tactics, techniques, motivations, and implications. For watch centers and fusion cells, it provides the structured context needed to detect, understand, and respond to hostile activity.

### Core Principles

- **Actionability:** Intelligence must be timely and relevant to operational decision making
- **Contextualization:** Raw indicators become intelligence only when placed in mission or threat context
- **Validation:** Information must be sourced, vetted, and assessed for confidence
- **Sharing:** Structured exchange improves collective defense, especially in cross-sector or coalition environments

---

## 2. Introduction to METEORSTORM

METEORSTORM (*Multiple Environment Threat Evaluation of Resources, Space Threats, and Operational Risk to Missions*) is a layered modeling and tagging framework built for converged domains spanning terrestrial, aquatic, aerial, orbital, and deep space.

### Core Exposure Domains

- Kinetic
- Non-kinetic
- Electronic Warfare (EW)
- Cyber Warfare
- Other (environmental)

### Beyond Tagging: The Broader METEORSTORM Functions

Although this guide focuses on applying the METEORSTORM tagging taxonomy to threat intelligence workflows, the framework itself is far more comprehensive. It integrates five interlocking core functions that support space mission resilience across the full threat lifecycle:

1. **Concept of Operations (CONOPS)** — defines operational context, mission objectives, and failure modes of interest
2. **Threat Modeling** — identifies relevant adversary behaviors, exposures, and attack surfaces
3. **Detection Engineering** — aligns telemetry, signatures, and analytic models to threat behaviors
4. **Incident Response Preparation** — supports pre-planned response pathways and contingency workflows
5. **Adversary Management** — provides a structured approach to understanding, tracking, and countering hostile actors

These functions establish METEORSTORM as an operational framework rather than merely a tagging convention. However, **the scope of this guide is limited to the application of METEORSTORM tags** for structuring, fusing, and sharing threat intelligence.

### Why METEORSTORM Matters

> "We needed a lexicon to convert the kaleidoscope of space platform elements into a periscope of platform exposure"
> 
> — ethicallyHackingspace(eHs)® Team

- It provides a **common language** for describing threats against complex, multi-domain systems
- It improves **discoverability and fusion** of operational and technical intelligence
- It is **tool-agnostic** but designed to map cleanly into MISP, TIPs, and STIX

---

## 3. METEORSTORM Layered Data Model

> **Note:** The framework uses the term *Aquatic* instead of *Maritime* to allow modeling beyond Earth-based maritime domains. This choice reflects METEORSTORM's support for both existing and hypothetical scenarios, including the representation of water bodies on other planets or moons. This intentional language selection provides analysts with greater flexibility when modeling multi-environment missions.

> **Note:** The framework also uses *Orbital* instead of *Space* as the Primary Capability Environment label to avoid confusion with the Space Segment. *Orbital* more accurately reflects the operational domain and provides a clear distinction between orbital and deep space environments.

The METEORSTORM data model is organized into five layers, each representing a distinct dimension of operational and analytic context. Each layer contains named elements with structured codes suitable for use in MISP taxonomies, STIX extensions, or other structured TI platforms.

---

### Layer One: Primary Capability Environment (PCE)

> "This layer was crucial as current frameworks simply skipped over mechanisms to operationalize key enrichment sources like Space Domain Awareness (SDA), terrestrial weather, maritime activity, and other environmental dimensions that need to be top of mind for analyst. No environmental context so how would you ever know if it was environmental or cyber physical?"
> 
> — ethicallyHackingspace(eHs)® Team

| Code | Name | Definition |
|:-----|:-----|:-----------|
| **PCE-TE** | Terrestrial | Surface-based operational zones on planetary bodies |
| **PCE-AQ** | Aquatic | Water-based operational zones, including maritime domains |
| **PCE-AE** | Aerial | Atmospheric operational zones spanning low, high, and near-space regions |
| **PCE-OR** | Orbital | Operational zones within planetary or satellite orbits |
| **PCE-DS** | Deep Space | Operational zones beyond planetary orbital regimes |

---

### Layer Two: Segment (SEG)

> "We had considered aerial, aquatic and other less frequently explored segments before the renewed focus on issues like oceanic cable attacks and rogue aerial platforms. These increased attack patterns simply codified that our approach to using the evolving adversary mindset to decompose systems made sense."
> 
> — ethicallyHackingspace(eHs)® Team

| Code | Name | Definition |
|:-----|:-----|:-----------|
| **SEG-LA** | Launch | Surface-based services and assets for primary launch operations |
| **SEG-LI** | Link | Services and assets enabling platform communications across signal paths |
| **SEG-GR** | Ground | Surface-based services and assets for primary platform operations, serving as the primary locus of control plane activity |
| **SEG-US** | User | Services and assets for primary end-user operations |
| **SEG-AQ** | Aquatic | Water-based services and assets for primary platform operations |
| **SEG-LO** | Low Altitude | Aerial services and assets in the lower atmosphere |
| **SEG-HI** | High Altitude | Aerial services and assets above the lower atmosphere but below near space |
| **SEG-NE** | Near Space | Aerial services and assets above high altitude and below orbital regions |
| **SEG-SP** | Space | Services and assets operating in planetary or satellite orbits |
| **SEG-DE** | Deep Space | Services and assets operating beyond planetary orbital regimes |

---

### Layer Three: Service (SVC)

> "Space systems are simply too diverse in terms of service definitions and descriptions. Grounding the service decomposition into control plane, data plane, and hybrid while allowing the platform owner to nest their organizational specific service definitions made the most sense."
> 
> — ethicallyHackingspace(eHs)® Team

| Code | Name | Definition |
|:-----|:-----|:-----------|
| **SVC-CP** | Control Plane | Services for managing and orchestrating platform control functions |
| **SVC-DP** | Data Plane | Services for managing and orchestrating mission product functions |
| **SVC-HY** | Hybrid | Services integrating both control and data plane functionalities |

---

### Layer Four: Asset (AST)

> "Space systems are simply too diverse in terms of asset definitions and descriptions. Grounding the asset decomposition into data, signal, hardware, firmware, software, and most importantly having a hybrid element to enable alignment with the concept of a 'subsystem' while allowing the platform owner to nest their organizational specific asset definitions made the most sense."
> 
> — ethicallyHackingspace(eHs)® Team

| Code | Name | Definition |
|:-----|:-----|:-----------|
| **AST-HW** | Hardware | Physical components supporting platform operations |
| **AST-FW** | Firmware | Embedded control code governing hardware functions |
| **AST-SW** | Software | Applications and logic executing operational tasks |
| **AST-DA** | Data | Information generated, processed, or consumed by the platform |
| **AST-SI** | Signal | Communication channels and transmission frequencies |
| **AST-HY** | Hybrid | Composite elements combining multiple asset types |

---

### Layer Five: Analytic (AN)

> "We had to focus on the key points without inducing analyst fatigue. Is something compromised, under attack, advertising an attack path, related to a specific threat and is there an available detection signature or resilience measure?"
> 
> — ethicallyHackingspace(eHs)® Team

Analysts need to quickly apply analytic enrichment elements to classify intelligence and determine its operational significance. This layer helps answer the critical questions that should be in every analyst's mind when processing threat intelligence:

- **Indicator of Compromise:** Has this system been compromised?
- **Indicator of Attack:** Is this system currently under attack?
- **Attack Path:** Is there a disclosed or known attack path that could be exploited?
- **Threat:** Is this platform being targeted by a specific threat or threat actor?
- **Detection Signature:** Is there an existing detection signature included with this intelligence?
- **Resilience Measure:** Is there a known resilience measure or mitigation included with this intelligence?

These questions guide analysts to quickly capture whether intelligence confirms system compromise, ongoing attacks, disclosed vulnerabilities, threat actor targeting, or provides actionable detection and defense capabilities.

| Code | Name | Definition |
|:-----|:-----|:-----------|
| **AN-ATT** | Attack Path | Known or modeled attack path for a converged space system |
| **AN-IOC** | Indicator of Compromise | Verifiable indication that the platform has been compromised |
| **AN-IOA** | Indicator of Attack | Verifiable indication that the platform has been targeted |
| **AN-THR** | Threat | Known or modeled threat to the platform |
| **AN-DET** | Detection Signature | Pattern, signal, or logic that triggers on contextualized threat behavior |
| **AN-RES** | Resilience Measure | Protective capability ensuring resistance or recovery from threats |

---

## 4. Fusion Concepts

Fusion is the process of combining information from multiple sources to produce a more complete and reliable threat picture.

### Intelligence Fusion in Practice

- **Ingest:** Collect internal telemetry, sensor data, and external intelligence feeds
- **Correlate:** Map disparate indicators to shared reference structures (e.g., METEORSTORM layers)
- **Enrich:** Add mission context, confidence levels, and cross-framework mappings
- **Disseminate:** Share back out to partners and operational elements

METEORSTORM tags act as **pivot points** in this cycle, enabling analysts to trace threat activity from environment down to asset level.

---

## 5. Threat Intelligence Platforms (TIPs)

A Threat Intelligence Platform (TIP) is software designed to aggregate, correlate, and share threat intelligence at scale.

### Typical TIP Capabilities

- Feed ingestion (STIX/TAXII, CSV, MISP)
- Normalization and de-duplication
- Tagging, scoring, and confidence enrichment
- Correlation across indicators
- Alerting, case management, and sharing

TIPs sit at the center of fusion cells, enabling **ingress and egress** of structured threat intelligence.

---

## 6. What is MISP?

MISP (Malware Information Sharing Platform) is an open-source TIP widely adopted across defense, space, and critical infrastructure communities.

### Key Features

- Event and attribute structure for structured threat intel
- Tagging and taxonomy support (e.g., METEORSTORM)
- TLP/PAP handling and sharing groups
- Correlation engine and warning lists
- STIX export for interoperability

MISP acts as the **reference backbone** for many national and sectoral sharing environments.

---

## 7. MISP Taxonomies

A **MISP taxonomy** is a structured tagging vocabulary used to label events and attributes in a way that is both human readable and machine parsable.

### Why Taxonomies Matter

- They provide **semantic consistency** across sharing partners
- They make it possible to **automate enrichment and correlation**
- They allow filtering, pivoting, and operational triage

The METEORSTORM taxonomy defines tags for PCE, SEG, SVC, AST, and AN, letting analysts map real-world incidents into structured categories.

---

## 8. Handling Threat Intelligence and Tagging Guardrails

Analysts must treat threat intelligence with both rigor and discipline.

### Good Practice Guidelines and Tagging Thresholds

- **Apply TLP/PAP markings first** to control dissemination
- **Validate source confidence** and information reliability
- **Record analytic judgments** and not just raw indicators
- **Maintain traceability** back to original observations
- **Use structured tags and taxonomies** to ensure your intelligence can be fused and re-used

### Tagging Guardrails

Over-tagging can reduce clarity, increase operational noise, and degrade the utility of threat intelligence feeds. To ensure tagging remains meaningful, analysts should:

- **Prioritize precision over volume:** Tag only those layers and elements that are directly relevant to the threat event or indicator
- **Apply no more than one or two PCE and SEG tags per indicator** unless multiple operational domains are demonstrably involved
- **Limit AN layer tagging** to the most relevant analytic dimension (e.g., ATT *or* THR, not all at once) unless the situation warrants a multi-tag context
- **Avoid redundant or speculative tags** that are not supported by evidence
- **Define a tagging threshold in the playbook:** For example, no more than 5–7 total METEORSTORM tags per MISP event unless justified with analytic notes
- **Document exceptions** in the event record when thresholds are exceeded

This ensures that tags remain analytically significant, machine-parsable, and operationally actionable.

---

## 9. Using METEORSTORM for Ingress and Egress TI

The METEORSTORM tagging model allows threat intel to **flow in and out of your environment** with structure and context.

### Ingress Workflow

1. Receive raw indicators or structured reports
2. Map indicators to **PCE, SEG, SVC, AST**, and **AN** tags
3. Record source confidence, exposure domain, and analytic evidence
4. Fuse with internal telemetry or mission data

### Egress Workflow

1. Select key findings and observables for sharing
2. Add METEORSTORM tags to encode structure
3. Attach TLP/PAP and confidence levels
4. Publish to partner environments (e.g., MISP, STIX feeds)

### Benefits

- Better automated correlation
- Easier fusion with external feeds
- Consistent language across partners
- Faster operational response

---

## 10. Recap & Practical Next Steps

- Threat intelligence gains value through **structure, fusion, and sharing**
- METEORSTORM provides a **layered model** for mapping activity to real mission surfaces
- TIPs and MISP enable **scalable intelligence exchange**
- Consistent tagging improves both **ingress** and **egress** flows

**Recommended practice:** Establish a baseline tagging playbook, train analysts on METEORSTORM layers, and implement a governance process for taxonomy updates.

---

## 11. Example Walkthrough: Tagging the Viasat Incident

The 2022 cyberattack against Viasat's KA SAT network illustrates how METEORSTORM tags can be applied systematically across layers to create structured, shareable threat intelligence.

### Step 1: Understand the Event Context

- The attack targeted ground infrastructure and modems supporting commercial and governmental customers
- Malicious activity involved wiping modem firmware, disrupting user services, and interfering with control plane operations
- Operational impact extended from terrestrial ground stations to orbital relay links

### Step 2: Identify Primary Capability Environments (PCE)

- **PCE-TE (Terrestrial)** — Ground network infrastructure and modem operations occurred on the surface
- **PCE-OR (Orbital)** — Satellite segment relayed communications to users and was operationally impacted

**Tagging decision:** Two environments (PCE-TE, PCE-OR) are directly relevant. Deep space or aquatic domains are not.

### Step 3: Identify Affected Segments (SEG)

- **SEG-GR (Ground)** — Ground stations and core network elements
- **SEG-LI (Link)** — Communications link between ground and orbital assets
- **SEG-US (User)** — End-user terminals and modems impacted by the wiper

**Tagging decision:** Three segments are appropriate; no need to tag launch or deep space segments.

### Step 4: Identify Service Layer Elements (SVC)

- **SVC-CP (Control Plane)** — Modem authentication, provisioning, and management were targeted
- **SVC-DP (Data Plane)** — User traffic routing was indirectly disrupted

### Step 5: Identify Affected Assets (AST)

- **AST-FW (Firmware)** — Modem firmware was wiped
- **AST-HW (Hardware)** — Modems were rendered inoperable
- **AST-SI (Signal)** — Signal path between modems and satellite disrupted

### Step 6: Analytic Layer (AN)

- **AN-ATT (Attack Path)** — Exploitation path: access to ground management infrastructure → pushing malicious update → modem impact
- **AN-THR (Threat)** — Actor behavior aligned with destructive, state-linked activity
- **AN-IOC (Indicator of Compromise)** — Hash of wiper binary, compromised management infrastructure artifacts

### Step 7: Apply Tagging Guardrails

- **PCE:** 2 tags (TE, OR)
- **SEG:** 3 tags (GR, LI, US)
- **SVC:** 2 tags (CP, DP)
- **AST:** 3 tags (FW, HW, SI)
- **AN:** 3 tags (ATT, THR, IOC)

**Total:** 13 tags. Justification documented since this exceeds the default 5–7 guideline.

### Step 8: Record and Disseminate

- Add tags to the MISP event along with TLP markings and confidence scoring
- Document attack chain narrative for traceability
- Share event with partner communities using consistent METEORSTORM tagging

---

## 12. Fictitious Intelligence Example: Operational Tagging and Event Table

### Tagging Guardrails in Practice

- **Prioritize precision over volume:** Only tag relevant operational layers
- **PCE and SEG limited:** One or two per indicator unless multi-domain impact
- **AN layer selective:** Use ATT or THR, avoid piling on unnecessary tags
- **5–7 tag threshold:** Exceptions documented with reasoning

### Fictitious Incident Summary

**Title:** KA-SAT modem disruption — coordinated infrastructure compromise  
**TLP:** Amber  
**Confidence:** High  

**Summary:** On 21 February 2022, malicious actors gained unauthorized access to ground-based management infrastructure supporting satellite modem provisioning. Malicious firmware updates were distributed to user modems, resulting in widespread service disruption across multiple regions.

### Key Indicators

- SHA256 hash of wiper binary: `abc12345fictitioushash67890`
- C2 domain: `mgmt-c2.fictional-ops.net`
- Compromised IP range: `192.0.2.0/24`
- Observed attack vector: authenticated API abuse with stolen credentials

### METEORSTORM Tagging Breakdown

- **PCE:** PCE-TE (Terrestrial), PCE-OR (Orbital)
- **SEG:** SEG-GR (Ground), SEG-LI (Link), SEG-US (User)
- **SVC:** SVC-CP (Control Plane), SVC-DP (Data Plane)
- **AST:** AST-FW (Firmware), AST-HW (Hardware), AST-SI (Signal)
- **AN:** AN-ATT (Attack Path), AN-THR (Threat), AN-IOC (Indicator of Compromise)

### Resulting Tag Set for the Fictitious Event

```
meteorstorm:PCE=PCE-TE
meteorstorm:PCE=PCE-OR
meteorstorm:SEG=SEG-GR
meteorstorm:SEG=SEG-LI
meteorstorm:SEG=SEG-US
meteorstorm:SVC=SVC-CP
meteorstorm:SVC=SVC-DP
meteorstorm:AST=AST-FW
meteorstorm:AST=AST-HW
meteorstorm:AST=AST-SI
meteorstorm:AN=AN-ATT
meteorstorm:AN=AN-THR
meteorstorm:AN=AN-IOC
```

### Analyst Reasoning Notes

- Multiple environments are tagged due to the propagation of impact from ground to orbital segments
- Link and User segments are included because firmware corruption propagated across the signal path
- Control and data planes were affected by both the initial exploit and subsequent disruption
- IoCs provide high-fidelity technical enrichment, while ATT and THR contextualize adversary behavior
- Total tag count = 13. Exceeds baseline threshold; justification documented in analyst notes

---

### MISP Event Table for 10 Fictitious Intelligence Entries

| Event ID | Title | Key Observable | PCE Tags | SEG Tags | SVC Tags | AST Tags | AN Tags | Reasoning / Justification |
|:--------:|:------|:---------------|:---------|:---------|:---------|:---------|:--------|:--------------------------|
| **1** | Initial Access via API | Compromised admin creds | PCE-TE | SEG-GR | SVC-CP | AST-SW | AN-ATT, AN-IOC | Targeted terrestrial ground infrastructure; no orbital impact yet |
| **2** | C2 Domain Established | mgmt-c2.fictional-ops.net | PCE-TE | SEG-GR | SVC-CP | AST-SW | AN-IOC | C2 strictly involved ground layer; no link or user segment affected |
| **3** | Lateral Movement | Internal management API pivot | PCE-TE | SEG-GR | SVC-CP | AST-SW | AN-ATT | Restricted to ground infrastructure control layer |
| **4** | Firmware Distribution | Malicious firmware push | PCE-TE, PCE-OR | SEG-GR, SEG-LI | SVC-CP | AST-FW | AN-ATT, AN-THR | Firmware update crossed terrestrial to orbital link. User segment not tagged yet |
| **5** | User Modem Impact | Modem firmware corruption | PCE-TE, PCE-OR | SEG-GR, SEG-LI, SEG-US | SVC-CP, SVC-DP | AST-FW, AST-HW | AN-ATT, AN-IOC | Direct user modem impact; threshold tagging justified |
| **6** | Signal Degradation | Modem-to-satellite signal failure | PCE-OR | SEG-LI, SEG-US | SVC-DP | AST-SI | AN-ATT | Link and user affected but no new control plane compromise |
| **7** | Threat Actor Attributed | Attribution statement | PCE-TE | SEG-GR | — | — | AN-THR | Only threat-level tag applied. No additional layers relevant |
| **8** | IoC Enrichment | New hashes identified | PCE-TE | SEG-GR | — | — | AN-IOC | IOC only—minimal tagging to preserve precision |
| **9** | Detection Signature Developed | New Snort signature published | PCE-TE | SEG-GR | SVC-CP | AST-SW | AN-DET | Derived signature from earlier telemetry. No user segment |
| **10** | Resilience Measure | Firmware hardening applied | PCE-TE | SEG-GR | SVC-CP | AST-FW | AN-RES | Resilience applied to ground infrastructure; no orbital or user layers affected |

---

### Tagging Rationale and Omissions

- **Avoiding broad tagging:** Events are tagged at the most directly affected layers only. Not every event touches all layers
- **Progressive escalation:** Early events are limited to PCE-TE, SEG-GR, later events expand to orbital and link layers
- **Analytic precision:** AN tags are applied deliberately. For example, Event 7 uses only AN-THR to avoid unnecessary tagging
- **Controlled IOC tagging:** IoCs (Events 2 and 8) are intentionally scoped to ground infrastructure
- **No over-tagging:** Most events stay well below the 5–7 tag threshold; Events 4 and 5 are documented exceptions

**Summary:** Distributing intelligence across multiple discrete MISP events, rather than aggregating all observables into a single over-tagged record, maintains fidelity, traceability, and analytic clarity.

---

## Document Information

**Framework:** METEORSTORM  
**Developed by:** ethicallyHackingspace(eHs)® Team  
**Version:** Tagging Guide v1.0  
**Last Updated:** 2025
