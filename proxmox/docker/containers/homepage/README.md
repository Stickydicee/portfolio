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
- My full stack configuration in [`docker-compose.yaml`](./yaml/docker-compose.yaml)
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

These files hold my compose YAML file, custom layout and service settings:

> 📁 `yaml/`
> - [`compose.yaml`](./yaml/compose.yaml) - used to deploy Homepage via Portainer as a Docker stack
>
> 📁 `yaml/config/`
> - [`bookmarks.yaml`](./yaml/config/bookmarks.yaml) – quick access to OSINT tools, docs, and personal references  
> - [`services.yaml`](./yaml/config/services.yaml) – all running services in my homelab, categorized by stack or function  
> - [`settings.yaml`](./yaml/config/settings.yaml) – UI behavior, layout and theme  
> - [`widgets.yaml`](./yaml/config/widgets.yaml) – system info, network and monitoring widgets

These files are actively updated to reflect the current state of my homelab.

---

📌 **Note**: All files and configurations are tailored to my personal setup and use case, but can easily be adapted to any homelab or self-hosted environment.
