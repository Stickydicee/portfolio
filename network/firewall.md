# ⚡️ Firewall Zones & Rules

This file explains how I currently use Unifi's firewall features in my homelab setup. As someone who is still learning about networking, I find Unifi's **zone-based firewall system** to be very accessible and beginner-friendly. It's well-integrated, clearly visualized, and gives you control without overwhelming complexity.

---

## 🔒 What are Firewall Zones in UniFi?

Unifi has integrated a **Zone-Based Firewall** model that simplifies firewall rule management. Instead of creating dozens of rules between specific devices or VLANs, you can assign VLANs or interfaces to zones (like `Internal`, `VPN`, `Hotspot`, etc.) and create broader rules **between zones**.

For someone like me who's still developing their networking skills, this helps reduce complexity and allows me to segment my network in a visual and logical way.

![Zone Explanation](./assets/firewall-zones-explanation.png)

---

## 🔹 Zone Overview

Most of the zones in my setup are **built-in defaults** from UniFi. The only custom zone I created myself is `Untrusted (Internet)`, which is used to segment untrusted IoT devices that still need internet access.

### Internal
- Contains: `Management`, `Main - Trusted`, `Server - Trusted`
- This is the zone where most of my trusted internal devices live.
- Devices here have access to other zones (by default).

In the future, I plan to separate `Main - Trusted` and `Server - Trusted` into their own zones so that `Internal` is reserved only for `Management`.

### External
- Contains: `Primary (WAN1)`, `Secondary (WAN2)`
- Default behavior is to **block** all inbound traffic.
- Allows response (return traffic) to other zones like Internal or VPN.

### VPN
- Contains: `WireGuard`
- This zone is used for my remote VPN access, so I can manage my lab when I'm not home.

### Hotspot
- Contains: `Guest`
- This is where guest devices go.
- Devices in this zone have limited access and must authenticate through the **landing page** (see: [hotspot.md](./hotspot.md)).

### Untrusted (Internet)
- Custom zone I created
- Contains: `IoT`
- These are devices I don’t trust with access to the rest of my network (e.g., smart TVs, video doorbells), but they still need internet access.

![Zone Table](./assets/firewall-zones.png)

---

## 🔹 Visual Zone Matrix

I really like how UniFi visualizes firewall policies between zones using a **zone matrix**:

![Zone Matrix](./assets/firewall-zone-matrix.png)

This gives you a clear overview of:
- How many policies exist between each zone pair
- What action is being taken (`Allow All`, `Block All`, `Allow Return`, etc.)
- Clicking each block shows you the related policies

---

## 🔒 Firewall Rules (Policies)

Firewall rules (UniFi calls them "Policies") define what is and isn’t allowed between zones.

You can define:
- Source and destination zones / VLANs / devices / IPs / MACs
- Protocol (e.g., TCP, UDP, ICMP)
- IP version (IPv4, IPv6)
- Source and destination ports
- And more advanced options

A rule also includes an **action**:
- `Allow`
- `Block`
- `Reject`

And then you can **specify direction** of traffic and what should be returned.

---

## 🔹 Example Rules in My Setup

As of now, I’ve only configured **a few essential rules** that I needed to get my core systems working properly:

![Firewall Rules](./assets/firewall-policys.png)

- Allow communication between `Home Assistant` and `Reolink HUB`
- Allow communication between `ServerTrusted` and `IoT`
- Block `Main - Trusted` from accessing `Management`

There is much more I can still do, but for now this setup is functional and secure enough for my needs.

---

## 🔹 Final Thoughts

As mentioned earlier, I haven’t fully explored everything firewall zones and rules can do. This is an area where I want to **invest more time** in the future.

That said, **UniFi makes it really accessible**. For someone new to networking, the interface feels a lot like Apple’s approach—simple, clean, and powerful without needing to be an expert.

Are they the best tools in the world? I can’t say. But they work really well for me.

---

_See also:_
- [vpn.md](./vpn.md) for remote access setup
- [wan.md](./wan.md) for WAN configuration and DNS setup
- [hotspot.md](./hotspot.md) for guest WiFi and captive portal
