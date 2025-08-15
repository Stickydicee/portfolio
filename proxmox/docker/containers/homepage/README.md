# 🧭 Homepage Dashboard

This documentation covers how I use [Homepage](https://github.com/gethomepage/homepage) as the central dashboard for my homelab environment.

---

## 🔍 What is Homepage?

**Homepage** is a self-hosted, customizable dashboard built with simplicity and flexibility in mind.  
It allows you to visually organize and monitor your self-hosted services, tools, bookmarks, and widgets — all in one place.

---

## 🧠 Why I Use Homepage

Homepage is the perfect fit for my homelab setup because:
- 🧩 It supports full **custom configuration via YAML files**
- 🔧 You can **customize everything**: layout, widgets, services, themes, icons, bookmarks, and more
- 🚀 It acts as a launchpad and **monitoring panel** for all of my important services
- 🖥️ Simple to edit, deploy, and maintain

---

## ⚙️ How I Deploy Homepage

I deploy Homepage as a **Docker stack** inside **Portainer**, using a `docker-compose.yaml` file.

You'll find:
- My full stack configuration in [`compose.yaml`](./yaml/compose.yaml)
- Guide on how to deploy the stack in Portainer in [`install-homepage`](./install-homepage.md)

---

## 🛠️ Configuration Workflow

Homepage uses easy-to-read and write `.yaml` files to configure:
- **Services** – display status and access with simple widgets
- **Bookmarks** – add links to tools like OSINT search engines or documentation
- **Widgets** – monitor system metrics like CPU, RAM and disk usage

I edit these YAML files using:
- 🧠 [Cursor](https://cursor.sh/) – my preferred editor for structure-aware code editing
- 🖥️ [MobaXterm](https://mobaxterm.mobatek.net/) – for quick file transfers and SSH into my LXC containers or Proxmox nodes

---

## 🔗 Linked Services & Bookmarks

I've linked multiple Docker containers and external services to my Homepage instance. Examples include:
- **Proxmox (Server - A & Server B)**
- **Portainer**
- **AdGuard**
- **UniFi**
- **Home Assistant**
- OSINT, Tooling and Social bookmarks 

This makes Homepage a one-stop interface for managing, launching, and observing all services in my homelab.

---

## ✅ Why Homepage Works Best for Me

- Everything is done **locally** and **under my control**
- It is **lightweight** and doesn't require a database
- Configuration is **modular** and **easy to maintain**
- I can **rebuild or migrate** in minutes using Docker + Portainer

---

## 📁 What's in This Folder

| File | Description |
|------|-------------|
| `install-homepage.md` | Instructions to deploy Homepage in Portainer |
| `compose.yaml` | Full docker-compose stack for Homepage |
| `bookmarks.yaml` | Custom bookmarks (e.g. OSINT tools, docs) |

---

📌 **Note**: All files and configurations are tailored to my personal setup and use case, but can easily be adapted to any homelab or self-hosted environment.
