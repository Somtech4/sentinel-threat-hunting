# 🔐 Microsoft Sentinel Threat Hunting & Identity-Centric Detection Engineering

Overview

This repository documents the design and validation of identity-focused threat detection and governance controls using:
Microsoft Sentinel
Microsoft Entra ID
Microsoft Defender
The objective was not to generate alerts, but to examine how detection quality, identity governance, and analyst workflow interact in a real-world SOC environment.
Security operations function as a system.
Detection logic, identity privilege design, and governance cadence collectively shape attacker success long before an incident is declared.
This project explores that system how identity hygiene and detection engineering reinforce each other to improve signal confidence and reduce operational noise.


## 🎯 Engineering Focus
This repository emphasises:
Signal quality over alert volume
High-fidelity identity detections mapped to MITRE ATT&CK
Governance controls that reduce blast radius before detection
SOC-aware trade-offs (precision vs fatigue, automation vs judgment)
All queries are designed to run within Microsoft Sentinel’s Hunting blade and can be operationalised into analytics rules.

## 🧠 Detection Philosophy
A detection that fires is not automatically useful.
A log that exists is not automatically intelligence.
Each query in this repository is intentionally:
Tuned to minimise false positives
Focused on high-impact attacker behaviour
Structured to be explainable to analysts and auditors
Designed with escalation clarity in mind

## What This Repository Covers

- Hands-on **KQL threat hunting queries** mapped to MITRE ATT&CK
- **Identity-driven detections** for privileged and high-risk accounts
- **Preventive governance controls** using Entra ID Access Reviews (Lab 2)
- Operational guidance grounded in SOC reality

You run these in Microsoft Sentinel’s **Hunting** blade.

You detect real threats.

You reduce blast radius.

## Queries

- brute_force_ad.kql — T1110 Brute Force on domain accounts
- impossible_travel.kql — T1078 Valid Accounts (compromised creds)
- rdp_lateral_movement.kql — T1021.001 Remote Desktop Protocol
- powershell_suspicious.kql — T1059.001 PowerShell execution
- kerberoasting.kql — T1558.003 Kerberoasting
- pass_the_hash.kql — T1550.002 Pass the Hash
- golden_ticket.kql — T1558.001 Golden Ticket
- dcsync_attack.kql — T1003.006 DCSync
- privilege_escalation.kql — T1078.004 Domain Accounts abuse
- anomalous_admin_logons.kql — T1078 Valid Accounts (off-hours)

## 📂 Threat Hunting Queries (MITRE ATT&CK Mapping)

| Query                        | Technique ID          | Tactic                  |
|------------------------------|-----------------------|-------------------------|
| brute_force_ad               | T1110                 | Credential Access       |
| impossible_travel            | T1078                 | Initial Access          |
| rdp_lateral_movement         | T1021.001             | Lateral Movement        |
| powershell_suspicious        | T1059.001             | Execution               |
| kerberoasting                | T1558.003             | Credential Access       |
| pass_the_hash                | T1550.002             | Lateral Movement        |
| golden_ticket                | T1558.001             | Credential Access       |
| dcsync_attack                | T1003.006             | Credential Access       |
| privilege_escalation         | T1078.004             | Persistence             |
| anomalous_admin_logons       | T1078                 | Privilege Escalation    |

Each query is designed to:
- Minimize false positives
- Focus on **high-impact attacker behavior**
- Be explainable to analysts and auditors



## 🏛 Identity Governance & Privileged Access Reviews (Lab 2)

### Why Identity Governance Lives in a Sentinel Repo

Most SOC incidents fail **before detection** — through over-privileged identities,
stale admin access, and weak governance.

This lab demonstrates how **identity governance acts as a preventive detection control**,
reducing attacker dwell time and blast radius *before Sentinel alerts ever trigger*.


### Lab Objective

Implement Microsoft Entra ID Access Reviews to enforce least privilege
and reduce standing administrative access in cloud environments monitored by Sentinel.


### What Was Implemented

- Access Reviews scoped to **privileged Azure AD roles**
- Review cadence aligned with **risk vs operational overhead**
- Explicit decision logging for audit and compliance
- Integration mindset: identity signals feeding Sentinel detections


### Governance vs Detection Trade-Offs

| Decision Area | Trade-Off |
|--------------|----------|
| Review Frequency | Security rigor vs reviewer fatigue |
| Scope | Broad coverage vs analyst signal quality |
| Automation | Speed vs contextual human judgment |

This lab intentionally balances **security control strength** with **SOC usability**.


### How This Improves Sentinel Detections

Identity governance strengthens detection engineering by:
- Reducing false positives from legitimate-but-unnecessary admin usage
- Making anomalous admin logons *actually anomalous*
- Improving confidence in alerts tied to T1078 (Valid Accounts)

Example synergy:
- `anomalous_admin_logons.kql` becomes higher fidelity when standing privilege is reduced.


## How to Use

1. Open Microsoft Sentinel
2. Go to Hunting
3. Create new query
4. Paste from queries/ folder
5. Run and bookmark


## 📊 Evidence & Screenshots

This repository includes visual evidence from a live Microsoft Sentinel
and Entra ID lab environment.

Screenshots are provided to demonstrate:
- Executed hunting queries and real results
- MITRE-aligned detection logic
- Identity governance configuration
- Audit-ready access review decisions

All screenshots are located in the `screenshots/` directory.


## 👥 Intended Audience
SOC Analysts seeking higher-fidelity signal
Detection Engineers optimising alert quality
Cloud Security Engineers designing identity-centric monitoring
Teams preparing for governance audits or SOC maturity uplift

## 🚀 Future Expansion
Automating identity anomaly scoring
Expanding governance-to-detection correlation
Converting high-fidelity hunts into production analytics rules
Integrating Defender XDR investigation workflows

## License

MIT License

Security engineering is the disciplined design of systems that reduce uncertainty under operational constraints.
