# 🔐 Day 4: Log Analysis & Brute Force Detection

---

## 🎯 Objective

To analyze system logs and detect failed login attempts indicating a brute force attack.

---

## 🛠️ Tools Used

* Linux (Kali / Ubuntu)
* journalctl
* SSH

---

## ⚙️ Commands Used

```bash
journalctl | grep "Failed password"
journalctl | grep ssh
journalctl --since "today"
journalctl | grep "Accepted password"
```

---

## 🔍 Attack Simulation

### 🔹 Local Attack

* Command used: `su root`
* Result: Authentication failure
* Observation: No IP address (local activity)

---

### 🔹 Remote Attack (SSH)

Commands used:

```bash
ssh rajvarma@127.0.0.1
ssh rajvarma@10.112.77.203
```

---

## 📊 Logs Observed

```text
Failed password for rajvarma from 10.112.77.203 port 22 ssh2
Failed password for rajvarma from 10.112.77.203 port 22 ssh2
Failed password for rajvarma from 127.0.0.1 port 22 ssh2
```

---

## 🧠 Analysis

* Multiple failed login attempts detected
* Same username (rajvarma) targeted
* Same IP (10.112.77.203) attempted multiple logins
* Attempts occurred within a short period

This behavior indicates a brute force attack attempt.

---

## 🚨 Detection Logic

* High frequency of failed login attempts
* Same source IP
* Same target user
* Rapid login attempts

---

## ✅ Conclusion

The activity is suspicious and matches brute force attack behavior.

* Remote IP: 10.112.77.203
* Local IP: 127.0.0.1

---

## 🔐 Mitigation

* Block attacker IP
* Enable fail2ban
* Use SSH key authentication
* Monitor logs regularly

---
