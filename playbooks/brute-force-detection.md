# Brute Force Detection Playbook

## Detection Signals
- Multiple failed logins (Event ID 4625) from same IP
- Failed logins across multiple accounts from same source
- Successful login after many failures (credential stuffing)
- Login attempts outside business hours

## Thresholds (adjust per environment)
- >10 failed logins in 5 minutes = investigate
- >50 failed logins in 10 minutes = block and alert
- Failed logins on admin accounts = immediate alert

## Step 1 — Triage
- Is it targeting one account or many?
- One source IP or distributed?
- Is the source IP internal or external?
- Did any attempt succeed?

## Step 2 — Investigate Successful Logins
- Check if login IP matches user's normal location
- Check what was accessed after login
- Look for data exfiltration or lateral movement

## Step 3 — Containment
- Block source IP at firewall/WAF
- Lock targeted accounts temporarily
- Force password reset if compromise suspected
- Enable MFA if not already active

## Splunk Query
