# Phishing Investigation Playbook

## Step 1 — Initial Triage
- Who received the email? One user or multiple?
- Did anyone click the link or open the attachment?
- Check email headers: sender IP, SPF/DKIM/DMARC status
- Extract URLs and attachments — do NOT open directly

## Step 2 — Email Header Analysis
- Check `Reply-To` vs `From` mismatch
- Look for lookalike domains (paypa1.com, micosoft.com)
- Tools: MXToolbox, Google Admin Toolbox

## Step 3 — URL/Attachment Analysis
- Submit URL to VirusTotal, URLScan.io
- Submit attachment to Any.run or Hybrid Analysis
- Check if URL is a credential harvesting page

## Step 4 — Containment
- Block sender domain in email gateway
- Quarantine the email from all mailboxes
- Reset credentials if user clicked and entered data
- Block malicious URL/IP in firewall/proxy

## Step 5 — Investigation
- Check proxy logs — did anyone visit the URL?
- Check EDR — was any file executed?
- Review login logs for anomalous access after click time

## Step 6 — Documentation
- Record: who, what, when, IOCs found, actions taken
- Escalate if credential compromise confirmed

## IOCs to Collect
- Sender email and IP
- URLs in email
- File hashes of attachments
- C2 domains if malware executed
