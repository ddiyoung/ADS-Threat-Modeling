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

## 4. Major Claims

- **(C1):** The extended TARA methodology achieves 100% coverage of all threat categories defined in UN Regulation No. 155 Annex 5 Part A. This is proven by the verification (E1) described in Section 5.1, whose results are reported in Table B.1 and Table B.2.

- **(C2):** The integration of MITRE ATLAS and OWASP Top 10 for LLMs identifies 29% more AI-specific risks (11 out of 38 checklist items) compared to baseline STRIDE-only TARA. This is proven by the comparative analysis (E2) described in Section 5.2.

- **(C3):** The proposed methodology attains an Extended Maturity Level (ML 3) in data-driven robustness under the D2TARA maturity model. This is proven by the maturity assessment (E3) described in Section 5.3 and illustrated in Figure 3.

## 5. Experiments / Verification

### (E1): UN R155 Annex 5 Coverage Verification [~30 human-minutes]

- **How:** Open `7. Derivation CheckList/Checklist.pdf` and cross-reference each checklist item (CL-01 through CL-38) against the UN R155 Annex 5 Part A threat categories. The paper's Table B.1 and B.2 provide the complete semantic mapping.
- **Expected Result:** Every Annex 5 threat category (items 1–32) is addressed by at least one checklist item, confirming 100% coverage **(C1)**.
- **Artifacts Used:** `7. Derivation CheckList/Checklist.pdf`

### (E2): Comparative Analysis — STRIDE vs. Extended TARA [~30 human-minutes]

- **How:**
  1. Open `3. Threat Scenario/Threat Scenario(STRIDE).pdf` and enumerate the threat scenarios identified by STRIDE alone.
  2. Open `3. Threat Scenario/Threat Scenario(ATLAS).pdf` and `Threat Scenario(OWASP).pdf` to identify the additional AI-specific and LLM-specific threats.
  3. Cross-reference with `7. Derivation CheckList/Checklist.pdf` — 11 checklist items (CL-19, CL-20, CL-25–CL-27, CL-28, CL-29, CL-31–CL-33, and related items) are exclusively derived from the ATLAS/OWASP extensions.
- **Expected Result:** 11 out of 38 total checklist items (≈29%) address AI-specific threats that cannot be identified through STRIDE alone **(C2)**.
- **Artifacts Used:** `3. Threat Scenario/`, `7. Derivation CheckList/Checklist.pdf`

### (E3): D2TARA Maturity Assessment [~20 human-minutes]

- **How:** Evaluate the data integration level across TARA sections by inspecting the traceability chain:
  1. **Standardization (CL 2):** Verify that `2. AttackLibrary/` contains structured references from five external data source categories (CVE, CWE, Papers, Standards, Technical Reports).
  2. **Integration (CL 3):** Trace the full pipeline — Attack Library → Threat Scenarios → Damage Scenarios → Attack Paths → Security Requirements → Checklists — confirming systematic integration across the DAMAGE, ATTACK, and RISK TREAT sections.
- **Expected Result:** The methodology satisfies CL 3 (Integration) for all three universally recognized data-driven TARA sections **(C3)**.
- **Artifacts Used:** All directories (1–7)

### End-to-End Traceability Check [Optional, ~15 human-minutes]

To further validate the artifacts, pick any checklist item in `7. Derivation CheckList/Checklist.pdf` and trace it backward through the entire TARA pipeline:

  - Checklist → Security Requirement (`6. Derivation Security Requirements/`)
  - Security Requirement → Attack Path (`5. Attack Path Analysis/`)
  - Attack Path → Threat Scenario (`3. Threat Scenario/`) + Attack Library (`2. AttackLibrary/`)
  - Threat Scenario → Asset in DFD (`1. DFD/`)

This confirms that every security control is grounded in a concrete threat identified through the extended TARA process.

## 6. Using These Artifacts as a Reference

Researchers and practitioners who wish to apply the extended TARA methodology to their own systems can follow these steps:

1. **Define your system architecture** using multi-level DFDs (see `1. DFD/` for examples at Level 0, 1, and 2).
2. **Construct an Attack Library** by collecting and categorizing attacks from CVEs, CWEs, academic papers, standards, and technical reports (see `2. AttackLibrary/` for our methodology and format).
3. **Identify threat scenarios** using the three frameworks in parallel:
   - STRIDE for traditional software/network threats
   - MITRE ATLAS for AI/ML-specific threats
   - OWASP Top 10 for LLMs if your system incorporates large language models
4. **Derive damage scenarios, attack paths, security requirements, and checklists** following the ISO/SAE 21434 TARA process flow demonstrated in directories 4–7.

## 7. License

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