# 🪤 Honeypot on Raspberry Pi 5 with Slack Alerts

This project sets up [Cowrie](https://github.com/cowrie/cowrie), an SSH honeypot, on a Linux host and integrates it with Slack for real-time alerts on malicious activity.

---

## ⚠️ Disclaimer
This honeypot is for educational and monitoring purposes only. It should always be deployed in an isolated, non-production environment. 
Do not use honeypots in environments where they could be mistaken for real infrastructure and ensure they comply with all local laws and regulations.

## 🎯 Objective
- Deploy a realistic SSH honeypot in a home network
- Monitor brute-force attacks and log malicious behavior
- Practice log analysis and basic alerting
- Explore future integration with Slack notifications

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

## 📈 Planned Next Steps
- Enable Slack integration via webhook on new login attempts
- Push selected logs to centralized dashboard (Grafana or ELK)
- Develop simple Python script for log parsing & alerting

---

## 🧠 Lessons Learned
- Importance of network isolation when deploying attack surfaces
- Common brute-force patterns and usernames (root, admin, test)
- Cowrie’s logging structure and how to extract relevant data

---

## 📸 Screenshots
*You can add screenshots of your Pi setup, dashboard or logs here later.*
```
