# 🐱‍💻 Kali Linux VM Installation Guide (VirtualBox)

This guide explains how I installed Kali Linux on a Windows host using VirtualBox.  
The setup is designed for learning, practicing ethical hacking, and exploring cybersecurity tools.

---

## 🧩 Structure

- **[Kali Install](#kali-install)** – Full guide from downloading Kali and VirtualBox to the first successful login screen  
- _More steps coming soon…_ (e.g., guest additions, networking, tools, snapshots)

---

## 📥 Kali Install

### 1. Download Kali Linux

- **Website**: [https://www.kali.org](https://www.kali.org)
- **File chosen**: `.iso` (64-bit version)

💡 _Why ISO & 64-bit?_  
The ISO is needed for booting inside VirtualBox.  
To check if your system supports 64-bit:  
`Control Panel → System & Security → System`.

---

### 2. Download & Install VirtualBox

- **Website**: [https://www.virtualbox.org](https://www.virtualbox.org)
- **Platform**: Windows host installer

💡 During installation:
- Confirm install location
- Click **Yes** on network interface warning
- Click **Install**, then **Finish**
- VirtualBox opens automatically

---

### 3. Create the VM (Expert Mode)

![Create VM](./assets/kali-install-0.png)

- **VM Name**: Kali  
- **ISO Image**: Select the `.iso` from Kali  
- **OS Type**: Linux → Debian (64-bit)

---

### 4. Configure Virtual Hardware

![Hardware](./assets/kali-install-1.png)

- **RAM**: 8192 MB  
  _(25% of host RAM, for smooth usage)_

- **CPU**: 6 cores  
  _(Host has 16 cores → safe limit is 8)_

More cores = better performance when using tools like Metasploit, Burp Suite, etc.

---

### 5. Create Virtual Hard Disk

![Disk](./assets/kali-install-2.png)

- **Location**: `C:\Users\nicky\VirtualBox VMs\Kali\Kali.vdi`  
- **Size**: 80 GB  
- **Type**: VDI  
- **Pre-allocate full size**: Disabled

---

### 6. Boot VM & Launch Kali Installer

Click the green **Start** arrow to boot the VM.  
In the boot menu, select **Graphical Install**.

---

### 7. Kali Installation Steps

Here’s what the graphical installer walks you through:

#### 🌍 Region & Language
- Choose your language, region (for time zone), and keyboard layout

#### 🔡 Hostname & Domain
- Set a **hostname** (e.g., `kali`)
- (Optional) Set a domain name

#### 🔐 Root Password
- Enter a **secure password** for the root user

#### 💽 Partition Disks
- Choose: `Guided - use entire disk`
- Kali detects the virtual disk automatically

🧱 **Partition layout**:
- Choose: `All files in one partition` (simple, good for test VMs)
- Then select: `Finish partitioning and write changes to disk`
- Confirm the disk write by selecting **Yes**

#### 📦 OS Installation
- Kali will now install the OS (takes several minutes)

#### 🔗 Network Mirror
- Choose **No** (not required for now)

#### 🧱 Install GRUB Bootloader
- Select **Yes** to install GRUB (bootloader)
- Select target device (usually `/dev/sda`)

---

### ✅ First Boot

When installation is finished, Kali reboots and shows a login screen.

![Login Screen](./assets/kali-welcome.png)

Login with:
- **Username**: `kali` _(or the user you created)_
- **Password**: The password you set during install

Now you should arrive at the Kali desktop:

![Kali Desktop](./assets/kali-home.png)

You’re now ready to begin your journey in the exciting world of hacking.

---

## 📝 Notes

- This VM is used for hands-on pentesting, OSINT, and cybersecurity tool testing  
- Future steps will include guest additions, networking setup, and a list of tools

---

## 🔄 Next Step

🔗 Continue to: `tools.md` _(coming soon)_ – overview of installed tools and configurations inside the Kali VM
