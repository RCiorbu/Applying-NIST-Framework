# Applying-NIST-Framework
# DDoS Incident Report & NIST CSF Alignment

This repository documents a **DDoS incident report** using the NIST Cybersecurity Framework (CSF) and provides supporting playbooks, policies, and monitoring examples

---

## NIST CSF Functions
- **Identify** → Root cause and vulnerabilities
- **Protect** → Hardening controls (firewall, MFA, ACLs)
- **Detect** → Alerts & baselines
- **Respond** → Playbook actions, comms, escalation
- **Recover** → Service restoration, PIR, customer comms

---

# Incident Report: Distributed Denial of Service (DDoS) Attack

## Summary
On March 15, 2025, the IT team detected an unusual surge in ICMP traffic targeting the corporate gateway. The flood originated from multiple global IP ranges, saturating available bandwidth and temporarily rendering customer-facing web services unreachable. This indicates a **Distributed Denial of Service (DDoS)** attack. No data exfiltration or internal compromise was detected, but uptime and availability were severely impacted.

---

## Identify
The incident response team confirmed that malicious actors used ICMP flooding to overwhelm external interfaces. Firewall logs and NetFlow data revealed sustained abnormal spikes. The root cause was inadequate rate-limiting and missing anomaly thresholds in our baseline monitoring.

---

## Protect
To strengthen defenses, the following measures were implemented:
- Firewall ICMP rate-limiting and geofencing of high-risk IP ranges
- Access Control Lists (ACLs) tightened to restrict unnecessary inbound traffic
- Multi-Factor Authentication (MFA) enforced for administrator logins
- Employee awareness training on incident response and escalation procedures

---

## Detect
The security team deployed:
- An **Intrusion Detection System (IDS)** with tuned DDoS signatures
- Firewall logging with aggregation in a **SIEM** for pattern analysis
- Custom monitoring alerts for ICMP traffic anomalies against baselines

---

## Respond
- Malicious IP ranges were blackholed at the firewall
- Bandwidth was temporarily scaled with upstream ISP assistance
- Security team isolated affected subnets to restore availability
- Incident was escalated to management and law enforcement was notified

---

## Recover
- Normal network operations were restored within 3 hours
- Customer communication issued regarding temporary downtime
- Backups verified with no data loss
- A **Post-Incident Review (PIR)** scheduled to refine thresholds, policies, and playbooks

# DDoS Response Playbook

## Roles
- **Incident Commander (IC)** – Oversees response
- **Network Engineer** – Firewall, ACL, ISP coordination
- **SOC Analyst** – Monitoring, SIEM, forensics
- **Communications Lead** – Internal & external comms

## Steps
1. Detect traffic anomaly via SIEM/monitoring
2. Validate attack indicators (firewall logs, NetFlow)
3. Escalate to Incident Commander
4. Apply firewall rules / ACL updates
5. Coordinate with ISP for traffic scrubbing
6. Notify stakeholders (management, customers, law enforcement if required)
7. Monitor recovery progress
8. Document actions in real time

## Post-Incident
- Run **Post-Incident Review**
- Update firewall baseline rules
- Adjust monitoring thresholds
- Provide staff refresher training

# Firewall Baseline Policy

- Block all inbound traffic by default, allow only required ports (80, 443, VPN)
- Apply ICMP rate limiting (max 10 pps from single source)
- Enable anti-spoofing and bogon filtering
- Review and update firewall configs quarterly

- 
# Access Control Policy

- Principle of Least Privilege (PoLP) for all accounts
- MFA mandatory for all administrator roles
- Quarterly access reviews with HR/IT
- Immediate revocation upon role change or termination


