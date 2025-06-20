# 🪤 Honeypot on Raspberry Pi 5 with Slack Alerts

This project sets up [Cowrie](https://github.com/cowrie/cowrie), an SSH honeypot, on a Linux host and integrates it with Slack for real-time alerts on malicious activity.

---

## ⚠️ Disclaimer
This honeypot is for educational and monitoring purposes only. It should always be deployed in an isolated, non-production environment. 
Do not use honeypots in environments where they could be mistaken for real infrastructure and ensure they comply with all local laws and regulations.

---

## 🔍 What Is a Honeypot?
A honeypot is a decoy system designed to lure cyber attackers. It simulates a vulnerable target, capturing and logging interactions to help analysts understand attacker behaviors, techniques, and motives.

---

## 🎯 Why Are Honeypots Important?

Honeypots are a proactive security tool that serve as a trap for attackers, offering insights that traditional detection systems may miss. They:
- Detect early threats before they impact production systems
- Log attacker behavior and tools in a controlled environment
- Support red team/blue team exercises
- Improve incident response readiness

---

## 🛠 Project Features
- ✅ Cowrie SSH honeypot listening on port 22
- ✅ Slack integration to send real-time alerts
- ✅ Alerts on login attempts, command execution, downloads, session start/end
- ✅ Extendable Python script for integration with Discord, email, or a SIEM

---

## 👨‍💻 For Cybersecurity Analysts

This project provides practical hands-on experience for:
- Blue team monitoring
- Threat intelligence gathering
- Detection engineering
- Log analysis
- Developing Python automation for SOC workflows
- Use it to simulate attacks, gather attacker TTPs, and improve detection rules.

---

## 📸 Screenshots
*You can add screenshots of your Pi setup, dashboard or logs here later.*
```
