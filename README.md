# SOC 2 Type II Trust Services Criteria Implementation

**Organization:** MedCore Health Systems
**Framework:** AICPA Trust Services Criteria (TSC) — SOC 2 Type II
**Trust Service Categories in Scope:** Security (CC), Availability (A), Confidentiality (C)
**System in Scope:** MedCore Electronic Health Records Platform (EHRP) v4.2.1
**Report Period:** April 1, 2025 – March 31, 2026 (12 months)
**Status:** Readiness Assessment Complete | Type II Audit Scheduled Q3 2026
**Last Updated:** April 2026

---

## Overview

This repository documents MedCore Health Systems' implementation of the AICPA Trust Services Criteria (TSC) for a SOC 2 Type II examination. As a regional healthcare provider processing Protected Health Information (PHI) for approximately 85,000 patients, MedCore undergoes SOC 2 evaluation to provide independent assurance to business partners, payers, and enterprise customers that its information security controls operate effectively over time.

The SOC 2 scope covers the MedCore EHRP v4.2.1 system and all supporting infrastructure, personnel, and processes that provide the system's services.

---

## Trust Services Categories Selected

| TSC Category | Selected | Rationale |
|-------------|----------|-----------|
| Security (CC) | YES | Required for all SOC 2 reports; foundational trust criteria |
| Availability (A) | YES | Healthcare system uptime critical; SLA commitments to clinical partners |
| Confidentiality (C) | YES | PHI and business confidential data protection requirements |
| Processing Integrity (PI) | No | Not applicable — EHRP is not a transaction processing system |
| Privacy (P) | No | HIPAA Privacy Rule governs privacy obligations; separate compliance program |

---

## Trust Services Criteria Summary

### CC — Common Criteria (Security)

| Criteria Group | Description | Status |
|---------------|-------------|--------|
| CC1 — Control Environment | Tone at top; governance; COSO framework | Implemented |
| CC2 — Communication and Information | Internal/external communication of policies | Implemented |
| CC3 — Risk Assessment | Risk identification, analysis, and response | Implemented |
| CC4 — Monitoring Activities | SIEM, vulnerability scans, audit reviews | Implemented |
| CC5 — Control Activities | Policies, procedures, controls over operations | Implemented |
| CC6 — Logical and Physical Access | Access control, authentication, physical security | Implemented |
| CC7 — System Operations | Incident detection, response, recovery | Implemented |
| CC8 — Change Management | SDLC, change approval, testing | Implemented |
| CC9 — Risk Mitigation | Vendor risk, insurance, contractual protections | Implemented |

### A — Availability

| Criteria | Description | Status |
|----------|-------------|--------|
| A1.1 | Capacity management to meet performance commitments | Implemented |
| A1.2 | Environmental protections and redundancy | Implemented |
| A1.3 | Recovery procedures tested to meet availability commitments | Implemented |

### C — Confidentiality

| Criteria | Description | Status |
|----------|-------------|--------|
| C1.1 | Confidential information identified and protected | Implemented |
| C1.2 | Confidential information disposed of properly | Implemented |

---

## Repository Structure

```
soc2-trust-services/
├── README.md                              # This file
├── cc/
│   ├── cc1-control-environment.md       # CC1: Governance and tone at the top
│   ├── cc6-logical-physical-access.md   # CC6: Access controls (most tested criteria)
│   └── cc7-system-operations.md         # CC7: Incident detection and response
├── availability/
│   └── availability-criteria.md         # A1: Availability commitments and controls
└── confidentiality/
    └── confidentiality-criteria.md      # C1: Confidentiality controls
```

---

## Key Personnel

| Role | Name |
|------|------|
| SOC 2 Program Owner | Jonathan E. Steele, CISO |
| ISSO / Controls Evidence Lead | Amara Osei |
| System Owner | Dr. Priya Nambiar, CIO |
| External Auditor (Type II) | Armanino LLP (engagement planned Q3 2026) |

---

## SOC 2 Audit Roadmap

| Milestone | Target Date | Status |
|-----------|-------------|--------|
| Internal readiness assessment | Q1 2026 | Complete |
| Control gaps remediated | Q2 2026 | In Progress |
| Type II observation period end | March 31, 2026 | Complete |
| Auditor engagement letter signed | May 2026 | Planned |
| Fieldwork / evidence collection | June-July 2026 | Planned |
| Draft SOC 2 Type II report | August 2026 | Planned |
| Final SOC 2 Type II report issued | September 2026 | Planned |

---

## Frameworks and Standards Referenced

- AICPA Trust Services Criteria (2017, updated 2022)
- COSO Internal Control — Integrated Framework (2013)
- NIST SP 800-53 Rev 5 (cross-referenced)
- ISO/IEC 27001:2013 (aligned ISMS serves as SOC 2 control evidence)
