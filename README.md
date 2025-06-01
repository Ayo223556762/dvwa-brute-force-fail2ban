# DVWA Brute Force + Fail2Ban Defense

This project demonstrates a real-world offensive + defensive cyber scenario:
- 🔴 **Attack:** Brute-forcing a login form using Hydra
- 🔵 **Defense:** Using Fail2Ban to detect and prevent repeated login attempts

---

## 🔴 Offense: Brute-Force with Hydra

### Tools used:
- Kali Linux
- Hydra
- DVWA (Damn Vulnerable Web App)

### Attack goal:
Crack weak passwords on DVWA's login form using a wordlist attack with Hydra.

### Hydra command used:
```bash

hydra -l admin -P /usr/share/wordlists/rockyou.txt 127.0.0.1 http-post-form "/DVWA/vulnerabilities/brute/:username=^USER^&password=^PASS^&Login=Login:Login failed"
Outcome: 
```

Hydra successfully discovered multiple weak passwords such as 123456, password, and letmein.

📸 See screenshots/hydra-output.png for results

🔵 Defense: Fail2Ban Setup
Tools used:
Fail2Ban – Monitors logs and bans IPs

Apache2 – Web server hosting DVWA

Custom Regex Filter – Detects login abuse in access logs

Linux Terminal Utilities – nano, systemctl, fail2ban-client

Objective:
Use Fail2Ban to detect brute-force attacks by reading Apache access logs and banning IPs after repeated failed login attempts.

### Jail configuration (`/etc/fail2ban/jail.local`)
```ini
[dvwa-brute]
enabled  = true
port     = http,https
filter   = dvwa-brute
logpath  = /var/log/apache2/access.log
maxretry = 3
findtime = 60
bantime  = 300
```

📸 See screenshots/fail2ban-status.png for status output

📸 Screenshots
File	Description
login-page.png	DVWA brute-force login form
hydra-output.png	Successful Hydra brute-force results
fail2ban-status.png	Fail2Ban jail and monitoring status

🧠 What This Demonstrates
Red team tactics: web login brute force

Blue team tools: Fail2Ban with Apache log monitoring

Log file analysis and regex filter creation

Lab setup and troubleshooting experience

Ethical hacking with defensive awareness

⚙️ Requirements
Kali Linux or Debian-based distro

Apache2

DVWA installed and configured

Hydra

Fail2Ban

👨‍💻 Author
Ayo Adejumo
Cybersecurity Graduate Student
Hands-on Red + Blue Team Lab
GitHub: @Ayo223556762

