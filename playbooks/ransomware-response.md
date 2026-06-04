# Ransomware Response Playbook

## Immediate Actions (First 15 Minutes)
- Isolate infected machine from network immediately
- Do NOT turn off — memory forensics may be needed
- Identify the ransomware variant (check ransom note, file extension)
- Alert management and IR team

## Step 1 — Identify Scope
- How many machines are affected?
- Is it spreading via network shares?
- Check Active Directory — is domain controller hit?
- Look for lateral movement in SIEM logs

## Step 2 — Identify Entry Point
- Check RDP logs (Event ID 4624, 4625)
- Check email logs for phishing 24-48 hrs before encryption
- Check VPN logs for unusual access
- Review EDR telemetry for initial execution

## Step 3 — Containment
- Disable affected accounts
- Block C2 IPs/domains at firewall
- Disable SMB if spreading via network
- Snapshot affected VMs for forensics

## Step 4 — Eradication
- Identify and remove ransomware binary
- Check for persistence: scheduled tasks, registry run keys, startup folders
- Reset all potentially compromised credentials

## Step 5 — Recovery
- Restore from clean backups (verify backup integrity first)
- Rebuild machines if backups unavailable
- Patch the exploited vulnerability before bringing back online

## Common Ransomware Families
| Family | Extension | Entry Method |
|--------|-----------|--------------|
| LockBit | .lockbit | RDP, phishing |
| BlackCat | .seko | VPN exploits |
| Ryuk | .ryk | Emotet → TrickBot |
| Conti | varies | Phishing, RDP |

## Key Event IDs to Check
- 4624 — Successful logon
- 4625 — Failed logon
- 4688 — Process creation
- 7045 — New service installed
