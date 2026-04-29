# SOC 2 — C1: Confidentiality Trust Services Criteria

**Document ID:** SOC2-CON-001
**Version:** 1.0
**Classification:** Confidential
**Owner:** Dr. Rachel Feinberg, Privacy Officer
**Reviewed By:** Jonathan E. Steele, CISO
**Observation Period:** April 1, 2025 – March 31, 2026

---

## Overview

MedCore Health Systems has selected the Confidentiality Trust Services Category for its SOC 2 examination due to the sensitive nature of Protected Health Information (PHI) and confidential business data processed within the EHRP. Business partners and payers require assurance that confidential information is identified, protected, and disposed of appropriately.

---

## Confidential Information Classification

MedCore classifies information across four tiers, with the top two tiers subject to confidentiality controls:

| Classification | Description | Examples | Confidentiality Controls |
|--------------|-------------|---------|------------------------|
| Restricted (PHI) | Highest sensitivity; regulated | Patient medical records, diagnoses, treatment notes | Full AES-256 encryption, RBAC, audit logging, BAA required |
| Confidential | High sensitivity; proprietary | Business contracts, financial records, IP | Encryption at rest, need-to-know access, NDA required for contractors |
| Internal | Medium sensitivity | Policies, procedures, org charts | Standard access controls; not shared externally without approval |
| Public | No sensitivity | Press releases, website content | No special controls |

---

## C1.1 — Confidential Information is Protected During the System Design, Development, Testing, and Change Process

**Criteria:** The entity identifies and maintains confidential information to meet the entity's objectives related to confidentiality.

### Controls Implemented

**Identification and Inventory:**
- Data Classification Policy establishes four-tier classification scheme
- PHI data flows documented in Data Flow Diagram (in medcore-health-systems/diagrams/)
- Data inventory maintained: identifies where each class of confidential data is stored, processed, and transmitted
- All databases containing PHI are tagged in AWS with DataClassification=Restricted tag

**Protection Controls:**
- PHI at rest: AES-256 encryption via AWS KMS (FIPS 140-2 validated)
- PHI in transit: TLS 1.3 enforced; no unencrypted transmission permitted
- Access restricted to personnel with documented business need; RBAC enforced via Okta
- PHI access logged in Splunk SIEM with user ID, timestamp, and action
- DLP (Microsoft Purview) monitors and blocks unauthorized PHI transmission
- BAAs required for all third parties receiving PHI (47 BAs in register)

**During Development and Testing:**
- PHI prohibited in development and test environments
- Synthetic data generator used for test datasets
- Developer access to production PHI requires CISO approval and is time-limited

**Evidence Items:**
- Data Classification Policy (v2.1, effective January 2026)
- AWS resource tagging compliance report (97% tag coverage; gaps remediated Q1 2026)
- Microsoft Purview DLP policy configurations and incident log
- BAA register (47 BAs, all current)
- Developer access log: 2 approved production access requests in observation period; both time-limited and logged

**Operating Effectiveness:** Effective throughout the observation period

---

## C1.2 — Confidential Information is Disposed of When No Longer Needed

**Criteria:** The entity disposes of confidential information to meet the entity's objectives related to confidentiality.

### Controls Implemented

**Data Retention Schedule:**
- PHI (medical records): 7 years from date of last treatment (exceeds HIPAA 6-year minimum)
- PHI (minors): Retained until patient turns 25, or 7 years, whichever is longer
- Financial records: 7 years
- Employee records: 7 years post-termination
- Security logs: 12 months online, 24 months archived
- Backup data: 35-day RDS snapshots; S3 lifecycle policies auto-delete after retention period

**Electronic Disposal:**
- Data lifecycle policies implemented in AWS S3 using lifecycle rules
- Automated deletion executes at end of retention period
- Deletion events logged to SIEM
- Database records soft-deleted (flagged as inactive) before hard deletion at retention expiry

**Physical Media Disposal:**
- On-premises storage media: NIST SP 800-88 compliant wiping (DoD 5220.22-M for HDDs; cryptographic erase for SSDs)
- Certificate of destruction maintained for each disposal event
- POS terminal hard drives: Cryptographically erased before decommissioning
- Paper PHI: Cross-cut shredding; Iron Mountain secure disposal service for bulk records

**Third-Party Data Destruction:**
- Vendor contracts include data destruction clauses
- Vendors required to provide certificates of destruction upon contract termination
- BAA termination triggers formal data destruction request to business associates

**Evidence Items:**
- Data Retention and Disposal Policy (DRP-001, v2.0)
- AWS S3 lifecycle rules configuration (verified quarterly)
- Media disposal log: 12 disposal events in observation period; all have certificates of destruction
- Iron Mountain service records (monthly collection)
- Vendor data destruction certificates: 3 received in observation period (2 vendor contracts terminated)

**Operating Effectiveness:** Effective throughout the observation period

---

## Confidentiality Incident Summary — Observation Period

| Incident | Date | Description | Resolution |
|---------|------|-------------|-----------|
| CI-2025-001 | June 2025 | DLP alert: staff member attempted to email unencrypted patient list to personal email | Blocked by DLP; employee counseled; no data exfiltration confirmed |
| CI-2025-002 | October 2025 | Unauthorized PHI access by departing employee on final day | Access terminated within 4-hour SLA; no downstream sharing; CISO review completed |
| CI-2025-003 | February 2026 | Business associate requested PHI file beyond BAA scope | Request denied; BAA reviewed and updated to clarify permitted uses |

**0 reportable breaches in the observation period. All three incidents were identified by controls and resolved without patient harm.**
