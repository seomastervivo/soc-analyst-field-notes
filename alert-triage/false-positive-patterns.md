# Common False Positive Patterns

## Brute Force Alerts
| Scenario | Why FP | How to Confirm |
|----------|--------|----------------|
| User locked out after password change | Old cached credentials | Check if single user, single device |
| IT admin running scripts | Automated credential testing | Whitelist known admin IPs |
| Vulnerability scanner | Scheduled scan activity | Confirm scan schedule with IT |

## Malware Alerts
| Scenario | Why FP | How to Confirm |
|----------|--------|----------------|
| Antivirus quarantine file | AV already handled it | Check if process was blocked |
| Dev tools flagged | Legitimate hacking tools used by pentesters | Confirm with team |
| PUA (Potentially Unwanted App) | Not actual malware | Check if business-approved |

## Phishing Alerts
| Scenario | Why FP | How to Confirm |
|----------|--------|----------------|
| Security awareness test email | Internal phishing simulation | Check with HR/security team |
| Newsletter with tracking pixel | Marketing email | Check sender reputation |
| Bulk email from CRM | Legitimate marketing tool | Verify sender domain |

## General Rules
- Always check the source IP reputation before escalating
- Correlate with user behavior — is this normal for them?
- Check if alert fired on the same host recently
- Look for corroborating evidence before calling it a true positive
