# Microsoft Sentinel Threat Hunting & Identity Governance

Practical threat hunting queries and identity governance controls for Microsoft Sentinel,
designed for real-world SOC environments.

This repository focuses on **detection quality, analyst workflow, and risk reduction** —
not just alert generation.

I treat security operations as a system:
detections, identity controls, and governance decisions all shape attacker success
*before* an alert ever fires.


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

## MITRE ATT&CK Mapping

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



## Identity Governance & Privileged Access Reviews (Lab 2)

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

## Who This Is For

- SOC Analysts who want **better signal**
- Detection Engineers focused on **quality over quantity**
- Security Engineers designing **cloud-native SOCs**
- Teams preparing for **audit, governance, or incident response maturity**

## Evidence & Screenshots

This repository includes visual evidence from a live Microsoft Sentinel
and Entra ID lab environment.

Screenshots are provided to demonstrate:
- Executed hunting queries and real results
- MITRE-aligned detection logic
- Identity governance configuration
- Audit-ready access review decisions

All screenshots are located in the `screenshots/` directory.

## License

MIT License

You hunt threats.

You protect domains.
