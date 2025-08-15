# 🐳 Running Docker in an LXC Container on Proxmox

This document explains how I installed Docker inside an LXC container on my Proxmox node using a helper script.  
It was a fast and clean way to get Docker up and running — including Docker Compose and Portainer.

---

## ⚙️ Installation via Community Script

To simplify the installation process, I used a community-maintained helper script directly in the shell of the Proxmox node:

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/community-scripts/ProxmoxVE/main/ct/docker.sh)"
```

> ⚠️ **Important:**  
> Before running scripts from the internet, **always check and understand what the script does**.  
> I personally reviewed the script, confirmed its safety, and trust its implementation for my own lab setup.

This script walks you through an **advanced setup** where you're asked whether to install Docker Compose and Portainer.

---

## 🧩 Docker Compose

I selected `Yes` to install Docker Compose.

**Docker Compose** is a tool that lets you define and manage multi-container applications using a single YAML file (`docker-compose.yml`).  
It simplifies the process of starting, stopping, and updating containers that depend on each other, such as a web server and a database.

---

## 🖥️ Portainer

I also chose to install **Portainer**, which is a web-based Docker management UI. It makes it easy to:

- View and manage running containers
- Create and modify volumes, networks and stacks
- Monitor logs and container metrics
- Pull new images and update containers

I find Portainer especially helpful as someone who’s still getting comfortable with Docker.  
Even though I aim to manage everything using the CLI in the future, Portainer currently provides a smooth and visual workflow.

> 💡 Portainer also includes a **template library** to deploy popular services with one click.  
> I personally avoid using the templates because I prefer to learn by setting everything up manually using Compose files.
