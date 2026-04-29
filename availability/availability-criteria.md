# SOC 2 — A1: Availability Trust Services Criteria

**Document ID:** SOC2-AVL-001
**Version:** 1.0
**Classification:** Confidential
**Owner:** Thomas J. Bridwell, Systems Administrator
**Reviewed By:** Jonathan E. Steele, CISO
**Observation Period:** April 1, 2025 – March 31, 2026

---

## Overview

MedCore Health Systems has selected the Availability Trust Services Category for its SOC 2 examination because clinical staff depend on continuous access to the EHRP for patient care delivery. System unavailability directly impacts patient safety and clinical outcomes.

MedCore's availability commitments are defined in Service Level Agreements with clinical partners and in the EHRP service description provided to users.

---

## Availability Commitments

| System Component | SLA Target | Measurement Period | Exclusions |
|-----------------|-----------|-------------------|-----------|
| EHRP Web Application | 99.9% uptime | Monthly | Scheduled maintenance windows (Sundays 2–4 AM) |
| Clinical Records Module | 99.9% uptime | Monthly | Scheduled maintenance |
| Patient Billing Portal | 99.5% uptime | Monthly | Scheduled maintenance |
| API Gateway | 99.95% uptime | Monthly | None |
| PHI Database (RDS) | 99.99% uptime | Monthly | AWS infrastructure events |

---

## A1.1 — Capacity Management

**Criteria:** The entity maintains, monitors, and evaluates current processing capacity and use of system components (infrastructure, data, and software) to manage capacity demand and to enable the implementation of additional capacity to help meet its objectives.

### Controls Implemented

**Infrastructure Capacity:**
- AWS Auto Scaling Groups configured for EHRP web tier, API tier, and application tier
- Scale-out triggers: CPU > 70% for 5 consecutive minutes
- Scale-in triggers: CPU < 30% for 30 consecutive minutes
- Maximum capacity: 10x current baseline (pre-authorized)
- Monthly capacity reviews conducted by Systems Administrator

**Database Capacity:**
- Amazon RDS PostgreSQL with Multi-AZ deployment
- Read replicas for reporting workloads (2 replicas, us-gov-east-1)
- Storage auto-scaling enabled: 500 GB current, auto-expands to 16 TB
- Connection pooling via PgBouncer to prevent connection exhaustion

**Monitoring:**
- AWS CloudWatch dashboards for CPU, memory, disk I/O, and network utilization
- Alerts at 75% capacity threshold; escalation at 90%
- Monthly capacity planning report reviewed by CIO and CISO

### Evidence Items

- AWS Auto Scaling Group configurations (captured April 2025, reviewed quarterly)
- CloudWatch capacity alerts (12 months of alert history)
- Monthly capacity planning reports (12 reports in observation period)
- Q3 2025: Auto Scaling triggered 7 times during peak billing period; all successful

**Operating Effectiveness:** Effective throughout the observation period

---

## A1.2 — Environmental Protections and Recovery

**Criteria:** The entity authorizes, designs, develops, implements, operates, approves, maintains, and monitors environmental protections, software, data backup processes, and recovery infrastructure to meet its availability commitments and system requirements.

### Controls Implemented

**Infrastructure Redundancy:**
- Multi-AZ deployment: EHRP deployed across us-gov-east-1a and us-gov-east-1b availability zones
- Automatic failover: RDS Multi-AZ failover tested and operational (< 60-second failover)
- Load balancer health checks: Unhealthy instances automatically removed from rotation
- On-premises systems: Redundant power (dual UPS, generator), redundant networking

**Data Backup:**
- RDS automated backups: Daily snapshots with 35-day retention
- S3 cross-region replication: EHRP data replicated to us-gov-west-1 within 15 minutes
- Object Lock (WORM): Audit logs and compliance records immutable for 7 years
- Manual snapshot before all major deployments

**Recovery Infrastructure:**
- Recovery Time Objective (RTO): 4 hours for full EHRP restoration
- Recovery Point Objective (RPO): 1 hour maximum data loss
- Warm standby in us-gov-west-1 region for DR activation
- BCP/DR runbooks documented and version-controlled

### Evidence Items

- AWS architecture showing Multi-AZ deployment
- RDS Multi-AZ configuration and last failover test (September 2025 — 47-second failover)
- S3 cross-region replication configuration and monitoring logs
- Daily backup completion logs (365 days — 100% backup success rate)

**Operating Effectiveness:** Effective throughout the observation period

---

## A1.3 — Recovery Procedures Tested

**Criteria:** The entity tests recovery plan procedures supporting system availability to meet its commitments and system requirements and addresses identified deficiencies.

### Controls Implemented

**Annual BCP/DR Tabletop Exercise:**
- Conducted November 2025
- Scenario: Ransomware attack causing complete EHRP unavailability
- Participants: CISO, CIO, ISSO, Systems Admin, Cloud Engineer, Clinical Operations Director
- Outcome: RTO of 3.5 hours (within 4-hour target); RPO of 45 minutes (within 1-hour target)
- Two gaps identified: Runbook for cross-region failover needed updating; DNS failover procedure unclear
- Both gaps remediated by January 2026

**Quarterly Backup Restore Testing:**
- Q2 2025 (June): EHRP database restore to isolated test environment — SUCCESS (2h 15m restore time)
- Q3 2025 (September): Full application stack restore — SUCCESS (3h 47m)
- Q4 2025 (December): Cross-region restore from us-gov-west-1 — SUCCESS (3h 22m)
- Q1 2026 (March): Database point-in-time restore — SUCCESS (1h 55m)
- All restore times within RTO targets

**Annual Penetration Test (Availability-Focused Testing):**
- DoS resilience tested by Optiv Security (November 2025)
- AWS Shield Advanced demonstrated effective DDoS mitigation
- No availability-impacting vulnerabilities identified

### Evidence Items

- DR Tabletop Exercise Report DTX-2025-001 (November 2025)
- Quarterly backup restore test reports (4 reports in observation period)
- Gap remediation records: 2 gaps identified November 2025; both closed January 2026

**Operating Effectiveness:** Effective throughout the observation period

---

## Availability Performance — Observation Period Summary

| Month | EHRP Uptime | Incidents | Root Cause | RTO Met? |
|-------|------------|-----------|-----------|---------|
| April 2025 | 99.98% | 0 | N/A | N/A |
| May 2025 | 99.95% | 1 | RDS connection pool exhaustion (15 min) | Yes |
| June 2025 | 99.99% | 0 | N/A | N/A |
| July 2025 | 99.97% | 1 | WAF false positive blocked valid traffic (8 min) | Yes |
| August 2025 | 100.00% | 0 | N/A | N/A |
| September 2025 | 99.99% | 0 | N/A | N/A |
| October 2025 | 99.96% | 1 | Auto Scaling delay during peak enrollment period (12 min) | Yes |
| November 2025 | 100.00% | 0 | N/A | N/A |
| December 2025 | 99.98% | 1 | Scheduled maintenance overrun (6 min) | Yes |
| January 2026 | 100.00% | 0 | N/A | N/A |
| February 2026 | 99.99% | 0 | N/A | N/A |
| March 2026 | 99.99% | 0 | N/A | N/A |
| **Average** | **99.98%** | **4 incidents** | | **All Yes** |

**SLA target of 99.9% exceeded in all 12 months of the observation period.**
