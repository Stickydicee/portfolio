# 🪤 Honeypot on Raspberry Pi 5 with Slack Alerts

This project sets up Cowrie, an SSH honeypot, on a Linux host and integrates it with Slack for real-time alerts on malicious activity.

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

## 🛠️ Setup Overview
- **Device:** Raspberry Pi 5
- **OS:** Raspberry Pi OS Lite (headless)
- **Tool:** [Cowrie](https://github.com/cowrie/cowrie)
- **Network:** Static IP via DHCP reservation, port 2222 forwarded from KPN router to the Pi (Cowrie listens on 2222 by default)
- **Security:** Isolated VLAN segment (optional), logging to local storage

---

## 📂 Key Files
- `cowrie.cfg`: Honeypot configuration file
- `cowrie.log`: Log file capturing attack attempts
- `install-notes.md`: Manual installation steps (optional)

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
