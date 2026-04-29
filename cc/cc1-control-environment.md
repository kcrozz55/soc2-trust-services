# SOC 2 — CC1 through CC9: Common Criteria Control Matrix

**Document ID:** SOC2-CC-001
**Version:** 1.0
**Classification:** Confidential
**Owner:** Amara Osei, ISSO
**Last Updated:** April 1, 2026
**Observation Period:** April 1, 2025 – March 31, 2026

---

## CC1 — Control Environment

The control environment sets the tone for the organization's commitment to security and forms the foundation of all internal controls.

### CC1.1 — COSO Principles: Demonstrates Commitment to Integrity and Ethical Values

**Control Description:** MedCore's Board and executive leadership establish and model ethical values and commitment to information security.

**Controls Implemented:**
- Code of Conduct published and signed annually by all employees
- CEO communicates security priorities in quarterly all-staff meetings
- Ethics hotline (1-800-555-0177) available for anonymous reporting of security violations
- Zero-tolerance policy for PHI misuse documented in employee handbook

**Evidence Items:**
- Code of Conduct v3.2 (signed by 1,198 of 1,198 eligible employees, January 2026)
- CEO Q1 2026 all-staff communication including security priorities
- Ethics reporting logs (10 reports filed FY2025; all investigated and closed)

**Operating Effectiveness:** Effective throughout the observation period

---

### CC1.2 — Board Exercises Oversight Responsibility

**Control Description:** MedCore's Board of Directors maintains oversight of the information security program.

**Controls Implemented:**
- Board Audit and Risk Committee receives quarterly cybersecurity briefings from CISO
- Annual Board approval of information security budget and program priorities
- Board charter includes explicit information security oversight responsibility

**Evidence Items:**
- Board Audit Committee meeting minutes (Q1-Q4 2025, Q1 2026) with security agenda items
- FY2026 cybersecurity budget approval (Board resolution BR-2025-047)
- Board charter Section 4.3 — Information Security Oversight

**Operating Effectiveness:** Effective throughout the observation period

---

### CC1.3 — Management Establishes Reporting Structure, Authority, and Accountability

**Control Description:** Management establishes an organizational structure with clear accountability for information security.

**Controls Implemented:**
- CISO reports directly to CEO with dotted-line to Board Audit Committee
- Information Security Steering Committee meets quarterly (CISO, CIO, Privacy Officer, Legal, HR)
- RACI matrix documents security responsibilities for all roles

**Evidence Items:**
- Organizational chart (February 2026 edition)
- RACI matrix ISO-ISMS-001 Appendix A
- Information Security Steering Committee meeting minutes (4 meetings in observation period)

**Operating Effectiveness:** Effective throughout the observation period

---

## CC2 — Communication and Information

### CC2.1 — Management Uses Relevant and Quality Information

**Controls Implemented:**
- Monthly security metrics dashboard reviewed by CISO and CIO
- H-ISAC threat intelligence feeds integrated into SIEM
- Annual enterprise risk assessment informs security investment decisions

**Evidence Items:**
- Monthly security metrics reports (12 reports in observation period)
- Splunk SIEM integration with H-ISAC threat feeds (configuration record)
- Enterprise risk register (updated Q4 2025)

**Operating Effectiveness:** Effective throughout the observation period

### CC2.2 — Internally Communicates Objectives and Responsibilities

**Controls Implemented:**
- Information security policies published on intranet; mandatory reading confirmed via LMS
- Annual security awareness training covers employee security responsibilities
- New hire orientation includes security briefing

**Evidence Items:**
- Intranet policy library access logs (1,198 unique users in observation period)
- KnowBe4 training completion records (94.2% within 30 days; 100% overall)
- New hire orientation checklist (215 new hires in observation period)

**Operating Effectiveness:** Effective throughout the observation period

---

## CC3 — Risk Assessment

### CC3.1 — Specifies Objectives with Sufficient Clarity

**Controls Implemented:**
- ISMS scope and objectives formally documented (ISO-ISMS-001)
- System security objectives defined in SSP (EHRP-SSP-v2.1)
- Security objectives aligned with HIPAA and organizational strategy

**Operating Effectiveness:** Effective throughout the observation period

### CC3.2 — Identifies and Analyzes Risk

**Controls Implemented:**
- Annual risk assessment using ISO 27005 methodology
- Risk register maintained with 7 identified risks, owners, and treatment plans
- Threat intelligence feeds inform quarterly risk updates

**Evidence Items:**
- Risk Assessment Report ISO-RTP-001 (February 2026)
- Risk register with 7 risks — all have assigned owners and treatment decisions

**Operating Effectiveness:** Effective throughout the observation period

---

## CC4 — Monitoring Activities

### CC4.1 — Evaluates and Communicates Internal Control Deficiencies

**Controls Implemented:**
- Internal audit conducted annually (ISO-AUD-001, January 2026)
- SIEM monitors control effectiveness continuously; alerts on anomalies
- Internal control deficiencies tracked in JIRA; owners assigned and monitored

**Evidence Items:**
- Internal Audit Report ISO-AUD-001 (February 2026): 0 major NCs, 3 minor NCs
- JIRA deficiency tracking — 3 minor NCs from internal audit: 2 in progress, 1 closed
- Monthly SIEM operational report (12 reports in observation period)

**Operating Effectiveness:** Effective throughout the observation period

---

## CC5 — Control Activities

### CC5.1 — Selects and Develops Control Activities

**Controls Implemented:**
- Controls selected based on NIST SP 800-53 Rev 5 HIGH baseline tailored to MedCore
- Control activities documented in policies and procedures (11 policies in library)
- Control implementation tracked in System Security Plan

**Operating Effectiveness:** Effective throughout the observation period

### CC5.2 — Selects and Develops General Controls Over Technology

**Controls Implemented:**
- Change management (CAB process) controls all production changes
- Software development lifecycle includes security gates
- CIS benchmark hardening applied to all CDE and production systems

**Operating Effectiveness:** Effective throughout the observation period

---

## CC6 — Logical and Physical Access Controls

### CC6.1 — Implements Logical Access Security Measures

**Controls Implemented:**
- Okta SSO with RBAC enforces least privilege access
- MFA required for all users: 100% privileged, 98% standard users
- CyberArk PAM controls privileged access with session recording
- Access provisioning via ServiceNow with manager + ISSO approval

**Evidence Items:**
- Okta tenant configuration showing MFA enrollment rates
- CyberArk session recording logs (12,847 privileged sessions in observation period)
- ServiceNow access request tickets (1,847 access requests processed in observation period)

**Operating Effectiveness:** Effective throughout the observation period

### CC6.2 — Prior to Issuing System Credentials and Granting Access, Authenticates Users

**Controls Implemented:**
- Identity verification required before provisioning access
- HR system integration with Okta for automated provisioning on hire
- 4-hour deprovisioning SLA enforced on termination

**Evidence Items:**
- Okta Lifecycle Management configuration
- Offboarding audit: 47 terminations in period; all deprovisioned within 4 hours

**Operating Effectiveness:** Effective throughout the observation period

### CC6.3 — Role-Based Access Controls

**Controls Implemented:**
- RBAC with 24 defined roles in EHRP
- Quarterly access certifications (4 reviews in observation period)
- Segregation of duties enforced: developer/admin roles separated

**Evidence Items:**
- Okta role definitions (24 roles, last updated December 2025)
- Q2-Q4 2025 and Q1 2026 access review records: 147, 152, 149, 153 accounts reviewed

**Operating Effectiveness:** Effective throughout the observation period

### CC6.6 — Security Measures Against Threats from Outside System Boundaries

**Controls Implemented:**
- AWS WAF with OWASP Core Rule Set blocking external attacks
- AWS Shield Advanced DDoS protection
- CrowdStrike Falcon EDR on all endpoints
- Proofpoint email filtering blocking phishing and malware

**Evidence Items:**
- AWS WAF logs: 847 blocked attacks in observation period
- CrowdStrike dashboard: 23 threats blocked, 0 breaches

**Operating Effectiveness:** Effective throughout the observation period

### CC6.7 — Restricts Transmission, Movement, and Removal of Information

**Controls Implemented:**
- Microsoft Purview DLP policies restrict unauthorized data transmission
- USB ports disabled via Group Policy
- Encrypted email required for external PHI transmission

**Evidence Items:**
- Microsoft Purview DLP policy configuration and incident log (3 incidents in period; all investigated)

**Operating Effectiveness:** Effective throughout the observation period

---

## CC7 — System Operations

### CC7.1 — Detects and Monitors Security Events

**Controls Implemented:**
- Splunk SIEM with 147 correlation rules
- AWS GuardDuty threat detection
- CrowdStrike behavioral detection
- 24/7 SOC monitoring (managed SOC via Arctic Wolf)

**Evidence Items:**
- Splunk correlation rule inventory
- GuardDuty findings log: 12 medium findings in period, all investigated and resolved
- Arctic Wolf monthly SOC reports (12 reports in observation period)

**Operating Effectiveness:** Effective throughout the observation period

### CC7.2 — Monitors System Components for Anomalies

**Controls Implemented:**
- AWS CloudWatch monitoring with automated alerts
- Network IDS monitoring all CDE traffic
- Behavioral analytics in SIEM for user activity

**Operating Effectiveness:** Effective throughout the observation period

### CC7.3 — Evaluates Security Events

**Controls Implemented:**
- SIEM triage process with severity classification
- On-call security analyst reviews critical alerts within 15 minutes
- Incident severity matrix documented in IR Plan

**Operating Effectiveness:** Effective throughout the observation period

### CC7.4 — Responds to Identified Security Incidents

**Controls Implemented:**
- IR Policy POL-IR-001 with playbooks for 8 incident scenarios
- CIRT team with defined roles and escalation procedures
- Post-incident reviews within 30 days

**Evidence Items:**
- Incident log: 18 security events in observation period; 5 required formal IR response; 0 breaches
- Post-incident review reports (5 reports in period)

**Operating Effectiveness:** Effective throughout the observation period

---

## CC8 — Change Management

### CC8.1 — Authorizes, Designs, Develops, Tests, and Implements Changes

**Controls Implemented:**
- Change Management Policy POL-CM-003
- Change Advisory Board (CAB) reviews all production changes
- Mandatory security review for changes to CDE and PHI-adjacent systems
- Emergency change procedures with post-implementation review

**Evidence Items:**
- ServiceNow change management tickets: 347 changes in observation period; 100% have CAB approval
- Emergency changes: 12 emergency changes; all had post-implementation review

**Operating Effectiveness:** Effective throughout the observation period

---

## CC9 — Risk Mitigation

### CC9.1 — Identifies, Selects, and Develops Risk Mitigation Activities

**Controls Implemented:**
- Risk Treatment Plan (ISO-RTP-001) with 7 risks and treatment decisions
- Cyber liability insurance ($10M coverage, Sentinel Re Group)
- BCP/DR Plan with tested recovery procedures

**Operating Effectiveness:** Effective throughout the observation period

### CC9.2 — Assesses and Manages Risks from Vendors and Business Partners

**Controls Implemented:**
- Third-Party Risk Management Policy POL-TP-001
- Vendor security questionnaires for all Tier 1 and Tier 2 vendors
- BAA register with 47 business associates
- Annual SOC 2 report review for critical cloud vendors

**Evidence Items:**
- Vendor risk assessments: 12 Tier 1 vendors assessed in observation period
- SOC 2 reports received and reviewed: AWS (SOC 2 Type II), Okta (SOC 2 Type II), CrowdStrike (SOC 2 Type II)
- BAA register (47 BAs, all current as of March 2026)

**Operating Effectiveness:** Effective throughout the observation period
