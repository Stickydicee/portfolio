# Installing Proxmox VE

> This guide explains how I installed [Proxmox VE](https://www.proxmox.com/en/proxmox-ve) on two physical computers to create a cluster setup (see [proxmox-cluster.md](proxmox-cluster.md)).

## Prerequisites

Before installing, I created bootable flash drives with the Proxmox VE ISO. The full process is documented in [create-installer.md](create-installer.md).

I used:
- A monitor with HDMI input
- Keyboard and mouse
- 2 physical computers

> ⚠️ **Important**: On both machines I had to disable **Secure Boot** in the BIOS before the installer would boot.

## How to Disable Secure Boot

### For Windows PCs (generic):

1. Reboot and press `DEL`, `ESC`, `F2` or `F10` during startup to access the BIOS, in my case it was `ESC`.
2. Navigate to `Security` or `Boot` tab.
3. Find and disable `Secure Boot`.
4. Save changes and exit.

### For Lenovo PCs:

1. Reboot and press `F1` (or `F2`/`DEL`) to enter BIOS, in my case it was `F1`.
2. Go to the **Security** tab.
3. Set **Secure Boot** to `Disabled`.
4. Save & exit.

---

## Booting the Proxmox Installer

1. Insert the bootable USB drive.
2. Open the **Boot Menu** by pressing `F12` (Lenovo) or `F10` on (Windows).
3. Select the USB drive to boot.

![Proxmox Welcome Screen](./proxmox-welcome.png)

Choose `Install Proxmox VE (Graphical)` and press **Enter**.

---

## Storage Selection

I selected my **NVMe SSD** and used the **ext4** filesystem for now.  
Although I plan to switch to **ZFS** later, ext4 works fine for my current setup:

- PC 1: NVMe + SATA
- PC 2: Only SATA

![Storage Selection](./proxmox-storage.png)

After selecting the correct drive and storage type, click **Next**.

---

## Location and Time Zone

Input the following:

- Country: **Netherlands**
- Time Zone: **Europe/Amsterdam**
- Keyboard Layout: **English (US)**

![Time Zone Selection](./proxmox-tz.png)

Then click **Next**.

---

## Admin Password and Email

Enter the root password and an email address for system alerts (e.g., backup notifications).

- Use a **strong password** for production setups.
- The email will receive important alerts.

![Admin Setup](./proxmox-admin.png)

Click **Next**.

---

## Network Configuration

Most values were already correct due to my switch configuration (ports 7 & 8 for Server - Trusted VLAN). See [ports.md](ports.md) and [vlan.md](vlan.md) for details.

I only had to update the **Hostname**:

- For single node, example: `pve.local`
- For clusters, example: `pve-1.local`, `pve-2.local`, etc.

If DHCP does not provide values, fill in:

- IP Address
- Netmask
- Gateway
- DNS Server

![Network Configuration](./proxmox-network.png)

Click **Next**.

---

## Summary

Review all information before installing.

![Summary](./proxmox-summary.png)

If everything looks good, click **Install**.

---

## Installation Process

Proxmox will now install and process all the configuration.

![Installing Proxmox](./proxmox-installing.png)

Once the install finishes, the system will **automatically reboot**.

> 🔌 At this point, I usually disconnect the monitor, keyboard, mouse, and USB drive. Just wait 5–10 minutes.

---

## Accessing the Web Interface

You can now access the server via URL in the browser: https://<your-ip>:8006

⚠️ Your browser might show a **"Potential Security Risk"** warning:

![Security Warning](./proxmox-risky.png)

This is expected since the certificate is self-signed. Click **Advanced** and continue.

---

## Login Screen

Use the following credentials:

- **Username**: `root`
- **Password**: *your configured root password*
- **Realm**: `Linux PAM standard authentication`

![Login to Proxmox](../proxmox/proxmox-url.png)

Once logged in, you should see the Proxmox dashboard. 🎉

---

>After installation, proceed to post-install configurations:  
>➡️ [post-install.md](post-install.md)


