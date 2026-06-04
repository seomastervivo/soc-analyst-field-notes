# Elastic/KQL Queries for Threat Hunting

## Failed Logins
event.code: "4625" and winlog.event_data.LogonType: "3"

## Encoded PowerShell
event.code: "4688" and process.name: "powershell.exe" and process.command_line: -enc

## Suspicious Parent-Child Process
process.parent.name: ("winword.exe" or "excel.exe") and process.name: ("cmd.exe" or "powershell.exe")

## New Local Admin Created
event.code: "4720" or event.code: "4732"

## RDP Lateral Movement
event.code: "4624" and winlog.event_data.LogonType: "10"

## Mimikatz Detection
process.name: "lsass.exe" and event.action: "accessed"
