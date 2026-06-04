# Linux Forensics Cheatsheet

## System Information
```bash
uname -a                    # Kernel version
uptime                      # System uptime
last                        # Login history
who                         # Currently logged in users
w                           # Active sessions
```

## Process Analysis
```bash
ps aux                      # All running processes
ps aux --sort=-%cpu         # Sort by CPU usage
lsof -i                     # Open network connections by process
netstat -tulnp              # Listening ports
ss -tulnp                   # Alternative to netstat
```

## File Investigation
```bash
find / -mtime -1            # Files modified in last 24 hours
find / -perm -4000          # SUID files (privilege escalation risk)
stat filename               # File metadata
md5sum filename             # Hash a file
sha256sum filename          # SHA256 hash
```

## Log Analysis
```bash
cat /var/log/auth.log       # Authentication logs
grep "Failed password" /var/log/auth.log   # Failed SSH logins
grep "Accepted" /var/log/auth.log          # Successful SSH logins
journalctl -u ssh           # SSH service logs
```

## Network
```bash
ifconfig / ip a             # Network interfaces
arp -a                      # ARP table
route -n                    # Routing table
tcpdump -i eth0             # Capture traffic
```

## Persistence Locations to Check
```bash
crontab -l                  # User cron jobs
cat /etc/crontab            # System cron
ls /etc/cron.d/             # Cron drop-in directory
cat /etc/rc.local           # Startup script
ls ~/.bashrc ~/.bash_profile # Shell startup files
```
