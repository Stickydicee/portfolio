# 🐱‍💻 Kali Linux VM Installation Guide (VirtualBox)

This guide explains how I installed Kali Linux on a Windows host using VirtualBox.

---

## 📥 1. Download Kali Linux

- **Website**: [https://www.kali.org](https://www.kali.org)
- **File chosen**: `.iso` (64-bit version)

🔍 _Why ISO + 64-bit?_  
The ISO is required to boot Kali inside VirtualBox.  
To check if your host supports 64-bit:
`Control Panel → System & Security → System`.

---

## 📦 2. Download & Install VirtualBox

- **Website**: [https://www.virtualbox.org](https://www.virtualbox.org)
- **File**: Windows host installer

💡 During installation:
- Choose install location
- Click **Yes** on network interface warning
- Click **Install**, then **Finish**  
- VirtualBox launches automatically

---

## 💻 3. Create a New VM

I used "Expert Mode" for more control.

![Create VM](./assets/kali-install-0.png)

- **VM Name**: Kali  
- **ISO Image**: Selected Kali `.iso`  
- **OS Type**: Linux → Debian → 64-bit

---

## ⚙️ 4. Configure Virtual Hardware

![Virtual Hardware](./assets/kali-install-1.png)

### 🧠 RAM
- **Set to**: 8192 MB  
- _Rule of thumb_: Allocate ~25% of total host RAM

### 🧠 CPU
- **Set to**: 6 cores  
- _Host has_: 16 cores → Safe to use up to 8 for VM  
- More cores = better performance with heavy tools like Metasploit

---

## 💾 5. Set Up Virtual Hard Disk

![Virtual Disk](./assets/kali-install-2.png)

- **Location**: `C:\Users\nicky\VirtualBox VMs\Kali\Kali.vdi`  
- **Size**: 80 GB  
- **Type**: VDI  
- **Pre-allocate full size**: Disabled (saves space)

---

## 🚀 6. Boot VM & Begin Kali Installation

Use the **Start** button to launch the VM.  
Choose **Graphical Install** when the boot menu appears.

This gives a user-friendly visual interface for:

- Language selection  
- Region/time zone  
- Keyboard layout

---

## ✅ 7. Installation Complete

![Kali Details](./assets/kali-install-done.png)

Final specs of the VM:

- **RAM**: 8192 MB  
- **CPU**: 6 cores  
- **Disk**: 80 GB  
- **Boot Order**: Optical > Disk > Floppy  
- **Graphics**: VMSVGA with 16 MB VRAM

---

## 📝 Notes

- This VM is used for hands-on pentesting, OSINT, and learning security tools  
- Guest Additions, NAT settings, and snapshots will be configured later

---

## 🔄 Next Step

🔗 Continue to: [tools.md](tools.md) _(coming soon)_ – list of tools used inside Kali Linux
