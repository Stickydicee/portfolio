# 🛠️ Homelab Network Configuration

This folder contains a complete overview of my homelab network configuration, deployed on UniFi hardware. The network is fully segmented using VLANs, with clearly defined firewall rules, DHCP reservations, port tagging, and secure remote access via WireGuard VPN.

Each component is documented separately to ensure modularity, scalability, and clarity. The configuration reflects a real-world setup for learning, experimentation, and secure remote management.

This documentation serves both as a personal reference and a knowledge resource for others interested in building structured and secure home networks.

---

## 📁 Structure

- [`vlans.md`](./vlans.md) – Overview of VLANs, subnetting decisions, and purpose of each network segment  
- [`ports.md`](./ports.md) – Port configuration for UniFi Gateway & Switch, VLAN tagging, and PoE usage
- [`firewall.md`](./firewall.md) – Firewall policies, inter-VLAN access, and security controls
- [`vpn.md`](./vpn.md) – VPN setup using UniFi Teleport and WireGuard for secure remote access
- `dhcp.md – DHCP configuration, static leases, and DNS assignment (AdGuard)
- [`ssid.md`](./ssid.md) – Wi-Fi SSIDs per VLAN, encryption types, visibility, and roaming
- [`hotspot.md`](./hotspot.md) – Captive portal configuration and branding for guest Wi-Fi access

---

> 🔐 All configuration examples are based on a **UniFi Gateway Ultra**, combined with a **managed UniFi switch (USW Lite 8 PoE)** and a **U6 Pro access point**.
