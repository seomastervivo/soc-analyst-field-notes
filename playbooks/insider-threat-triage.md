# Insider Threat Triage Playbook

## Behavioral Indicators
- Large data downloads outside business hours
- Accessing files unrelated to job role
- Emailing files to personal accounts
- USB usage on sensitive systems
- Account active after resignation/termination

## Step 1 — Initial Detection
- DLP alert fired? What data was involved?
- UEBA anomaly score elevated?
- HR flagged the employee? (terminated, PIP, grievance)

## Step 2 — Investigation (Covert)
- Do NOT alert the user — investigation must be silent
- Pull DLP logs, proxy logs, email logs
- Check file access logs on file servers
- Review print logs and USB device logs

## Step 3 — Evidence Collection
- Document all findings with timestamps
- Preserve logs before they rotate
- Do not modify any evidence
- Involve legal/HR/management before taking action

## Step 4 — Containment
- Quietly revoke unnecessary access
- If imminent risk: disable account with management approval
- Preserve forensic image of workstation

## Key Evidence Sources
- DLP alerts
- Email gateway logs
- Proxy/web logs
- Active Directory access logs
- File server audit logs
- Endpoint DLP (USB, print)
