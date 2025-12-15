# sentinel-threat-hunting
# Microsoft Sentinel Threat Hunting Queries

10 practical KQL queries for Active Directory and MITRE ATT&CK detection.

You run these in Sentinel Hunting blade.

You detect real threats.

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

## How to Use

1. Open Microsoft Sentinel
2. Go to Hunting
3. Create new query
4. Paste from queries/ folder
5. Run and bookmark

##  Results



## License

MIT

You hunt threats.

You protect domains.
