# Alert Priority Matrix

## Priority Levels

| Priority | Response Time | Examples |
|----------|--------------|---------|
| P1 - Critical | Immediate (< 15 min) | Ransomware, Active breach, DC compromise |
| P2 - High | < 1 hour | Confirmed malware, Credential theft, Data exfil |
| P3 - Medium | < 4 hours | Phishing clicked, Brute force success, Suspicious lateral movement |
| P4 - Low | < 24 hours | Failed phishing, Brute force (failed), Policy violations |
| P5 - Informational | Log and monitor | Recon activity, Port scans, FP-likely alerts |

## Escalation Criteria
Escalate to P1 immediately if:
- Domain controller or AD is involved
- Data exfiltration confirmed
- Ransomware encryption active
- Executive accounts compromised
- Critical infrastructure affected

## Do Not Escalate If:
- Single failed login with no follow-up activity
- Known vulnerability scanner IP
- Alert already handled by EDR automatically
- Confirmed internal security testing
