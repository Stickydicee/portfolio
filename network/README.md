# 🛠️ Homelab Network Configuration

This folder documents the full network setup of my homelab environment, built on UniFi hardware. The network is segmented using VLANs, secured with strict firewall rules, and includes features like DHCP reservations, port-specific configurations, and a WireGuard VPN for remote access.

This documentation serves both as a personal reference and to share insights with others interested in secure and modular home networking.

## 📁 Structure

- `vlans.md` – Overview of VLANs, subnetting, and purpose
- `ports.md` – Switch port configuration and tagging per VLAN
- `firewall.md` – Firewall policies, inter-VLAN rules, and block lists
- `vpn.md` – WireGuard VPN setup and external access configuration
- `dhcp.md` – DHCP ranges, static leases, and DNS handling
- `ssid.md` – Wi-Fi SSIDs and their VLAN assignments

> All configuration examples are based on a UniFi Gateway Ultra setup, combined with a managed UniFi switch and U6 Pro access point.
