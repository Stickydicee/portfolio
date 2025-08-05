# 🖥️ Proxmox Setup & Configuration

This folder documents how I installed and configured Proxmox on my homelab hardware.  
The focus of this documentation is entirely on getting Proxmox up and running from bootable USB creation to a functional hypervisor setup, with correct storage and backup configuration.

This setup serves as the foundation for future virtual machines (VMs), LXC containers and service deployments.

---

## 📁 Structure

- **bootable.md** – How I created a bootable flash drive to install Proxmox on bare-metal devices
- **installation.md** – Installation walkthrough for Proxmox on each machine
- **post-install.md** – Essential steps after installation (updates, repositories, etc.)
- **storage.md** – Storage layout, disk configuration and ZFS considerations
- **backup.md** – Automatic backup setup and retention strategy

---

🔒 The configuration is designed around real-world usage, using a **Lenovo M720Q** and **HP EliteDesk 800 G2** as nodes in the cluster and includes dashboards for visibility and learning
