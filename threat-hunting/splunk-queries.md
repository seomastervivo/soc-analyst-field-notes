# Splunk Queries for Threat Hunting

## Brute Force Detection
index=windows EventCode=4625
| stats count by src_ip, user
| where count > 10
| sort -count

## Successful Login After Multiple Failures
index=windows EventCode=4625 OR EventCode=4624
| transaction user maxspan=10m
| where eventcount > 5 AND EventCode=4624

## Unusual Process Execution
index=windows EventCode=4688
| where ParentImage IN ("winword.exe","excel.exe","powerpnt.exe")
| table _time, user, Image, ParentImage, CommandLine

## PowerShell Encoded Commands
index=windows EventCode=4688 Image="powershell"
| where like(CommandLine, "%-enc%") OR like(CommandLine, "%-encoded%")
| table _time, user, CommandLine

## Lateral Movement via PsExec
index=windows EventCode=7045 ServiceName="PSEXESVC"
| table _time, host, user

## Large Data Transfers
index=proxy
| stats sum(bytes_out) as total_bytes by src_ip, dest_domain
| where total_bytes > 100000000
| sort -total_bytes

## DNS Queries to Suspicious Domains
index=dns
| stats count by query
| where count < 3
| search query=".xyz" OR query=".top" OR query="*.ru"

