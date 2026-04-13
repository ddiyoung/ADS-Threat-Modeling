# Artifacts for "A Study on Extending the TARA Methodology for Physical AI: A Case Study of ADS"

**Paper:** A Study on Extending the TARA Methodology for Physical AI: A Case Study of ADS

**Authors:** Jihun Woo, Junhyeong Lee

**Venue:** USENIX VehicleSec 2026

---

## 1. Overview

This repository contains the complete dataset artifacts for our extended Threat Analysis and Risk Assessment (TARA) methodology applied to an Automated Driving System (ADS) on the NVIDIA Jetson platform. The methodology integrates STRIDE, MITRE ATLAS, and OWASP Top 10 for LLMs within an ISO/SAE 21434-compliant process.

These artifacts serve two purposes:

1. **Reproducibility** — Reviewers can trace every claim in the paper (e.g., 100% UN R155 Annex 5 coverage, 29% additional AI-specific risks, 38 security checklists) back to the underlying data provided here.
2. **Reusability** — Practitioners and researchers conducting TARA or threat modeling for other Physical AI / ADS architectures can use these artifacts as a reference template, adapting the DFDs, Attack Library, and checklist derivation process to their own systems.

## 2. Directory Structure

```
├── 1. DFD/
│   ├── Level 0.png          # System context diagram
│   ├── Level 1.png          # Subsystem-level DFD
│   └── Level 2.png          # Component-level DFD
│
├── 2. AttackLibrary/
│   ├── Attack.pdf            # Consolidated Attack Library
│   └── Attack/
│       ├── CVE.pdf           # CVE-based attack references
│       ├── CWE.pdf           # CWE-based weakness references
│       ├── Paper.pdf         # Academic paper-based attack references
│       ├── Standard.pdf      # Standard-based references
│       └── Technical Report.pdf  # Technical report-based references
│
├── 3. Threat Scenario/
│   ├── Threat Scenario(STRIDE).pdf   # Baseline threat scenarios (Table 3)
│   ├── Threat Scenario(ATLAS).pdf    # AI-specific threats via MITRE ATLAS (Table 4)
│   └── Threat Scenario(OWASP).pdf    # LLM-specific threats via OWASP Top 10 (Table 5)
│
├── 4. Damage Scenario/
│   └── Damage Scenario.pdf   # Impact analysis and damage scenarios (Table 6)
│
├── 5. Attack Path Analysis/
│   └── Attack Path.pdf       # Traceability: Threat + Attack Library + Damage (Table 7)
│
├── 6. Derivation Security Requirements/
│   └── Security Requirement.pdf  # Security requirements per threat (Table 8)
│
└── 7. Derivation CheckList/
    └── Checklist.pdf          # 38 actionable security checklists (CL-01 to CL-38)
```

Each directory corresponds to a step in the extended TARA process (Sections 3–4 of the paper). All documents are provided in PDF format.

## 3. System Requirements

- **Hardware:** None required.
- **Software:** A PDF reader (e.g., Adobe Acrobat, any web browser).

No code execution is needed — these artifacts are analytical datasets.

## 4. Paper-to-Artifact Mapping

The table below shows which files correspond to which parts of the paper, so reviewers can locate the full underlying data behind any table or figure.

| Paper Section | Table / Figure | Artifact |
|---------------|---------------|----------|
| 4.1 Asset Identification | Figure A.1–A.3 | `1. DFD/` (Level 0, 1, 2) |
| 3.2 Attack Library Construction | Table 1 | `2. AttackLibrary/` |
| 4.2 Threat Scenario (STRIDE) | Table 3 | `3. Threat Scenario/Threat Scenario(STRIDE).pdf` |
| 4.2 Threat Scenario (ATLAS) | Table 4 | `3. Threat Scenario/Threat Scenario(ATLAS).pdf` |
| 4.2 Threat Scenario (OWASP) | Table 5 | `3. Threat Scenario/Threat Scenario(OWASP).pdf` |
| 4.3 Impact Rating | Table 6 | `4. Damage Scenario/Damage Scenario.pdf` |
| 4.4 Attack Path Analysis | Table 7 | `5. Attack Path Analysis/Attack Path.pdf` |
| 4.5 Security Requirements | Table 8 | `6. Derivation Security Requirements/Security Requirement.pdf` |
| 4.6 Checklist Derivation | Table A.4, A.5 | `7. Derivation CheckList/Checklist.pdf` |
| 5.1 Legal Coverage | Table B.1, B.2 | `7. Derivation CheckList/Checklist.pdf` (mapped to UN R155 Annex 5) |

The paper's tables present representative examples; the artifacts here contain the **complete, unabridged datasets**.

## 5. How to Use This Dataset

### 5.1 Reproducing the ADS Case Study

These artifacts are the complete output of our case study (Section 4). Since the TARA process is an analytical methodology — not a computational experiment — **the dataset itself is the result**. Reviewers can verify the paper's findings by:

1. Opening any artifact and confirming that the paper's tables are faithful subsets of the full data.
2. Tracing any checklist item (e.g., CL-25) backward through the entire pipeline to verify end-to-end traceability:

```
CL-25 (Checklist)
  → Security Requirement (6. Derivation Security Requirements/)
    → Attack Path (5. Attack Path Analysis/)
      → Threat Scenario (3. Threat Scenario/) + Attack Library (2. AttackLibrary/)
        → Asset in DFD (1. DFD/)
```

### 5.2 Reusing for ADS Threat Modeling

Researchers or practitioners conducting TARA on an ADS — whether on the same NVIDIA Jetson platform or a similar architecture — can directly reuse or extend the following artifacts:

- **Attack Library** (`2. AttackLibrary/`) — The library is constructed from CVEs, CWEs, academic papers, standards, and technical reports relevant to ADS. It can be used as-is for any ADS sharing similar components (camera, LiDAR, radar, MLLM, sensor fusion), or filtered/extended for a specific target system.
- **Threat Scenarios** (`3. Threat Scenario/`) — The STRIDE, ATLAS, and OWASP threat scenarios are derived per asset type. For an ADS with the same perception-planning-control architecture, these scenarios serve as a baseline that can be adopted or adapted.
- **Checklist** (`7. Derivation CheckList/`) — The 38 security checklists are validated against UN R155 Annex 5. They can be used directly as a compliance checklist for ADS cybersecurity assessment or Vehicle Type Approval (VTA) preparation.

### 5.3 Adapting to Other Physical AI Systems

For systems beyond ADS (e.g., autonomous drones, robotic surgery, smart manufacturing), the artifacts serve as a **reference template** for applying the extended TARA methodology:

1. **Define your system architecture** using multi-level DFDs (see `1. DFD/` for the format and decomposition approach).
2. **Build or extend the Attack Library** — the CVE/CWE/Paper structure in `2. AttackLibrary/` can be reused for shared components (e.g., GPU, OS, sensors) and supplemented with domain-specific entries.
3. **Apply the three-framework threat identification** in parallel:
   - STRIDE for software/network threats
   - MITRE ATLAS for AI/ML-specific threats
   - OWASP Top 10 for LLMs (if applicable)
4. **Follow the TARA pipeline** (directories 4–7) as a process template to derive damage scenarios, attack paths, security requirements, and checklists for your target system.

## 6. License

This dataset is released under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to share and adapt this material for any purpose, provided you give appropriate credit. If you use these artifacts in your work, please cite:

```bibtex
@inproceedings{woo2026tara,
  title     = {A Study on Extending the TARA Methodology for Physical AI: A Case Study of ADS},
  author    = {Woo, Jihun and Lee, Junhyeong},
  booktitle = {Proceedings of the USENIX Workshop on Vehicle Security (VehicleSec)},
  year      = {2026}
}
```