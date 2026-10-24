# MikroTik VLAN & IP Assignment: My Practice Walkthrough

I'm a college student getting into networking, and I've started learning MikroTik RouterOS. This repo is my first write-up: how I created a VLAN interface on a MikroTik router and assigned an IP address to it, with screenshots from my own practice.

I wrote it mostly for myself, so I can come back to it later. If it helps someone else who's just starting out, even better.

## What's inside

- **[MikroTik_VLAN_and_IP_Assignment_Walkthrough.pdf](MikroTik_VLAN_and_IP_Assignment_Walkthrough.pdf)** is the full step-by-step guide (7 pages).
- **screenshots/** has the four screenshots I used while practicing.

## What the walkthrough covers

1. **Creating a VLAN interface** (Interfaces → VLAN → New)
   - Name: `indadul-FNA`
   - VLAN ID: `3031`
   - Parent interface: `10G-SFP+`
2. **Assigning an IP address to the VLAN** (IP → Addresses → New)
   - Address: `11.10.10.2/30`
   - Interface: the VLAN I just created
3. **The same thing from the CLI**, because the GUI is nice but the terminal is faster:

   ```
   /interface vlan add name=indadul-FNA vlan-id=3031 interface=10G-SFP+
   /ip address add address=11.10.10.2/30 interface=indadul-FNA
   ```

4. How to **verify** it worked (ping the peer, check the route, use torch)
5. A few **mistakes to avoid** that I ran into or noticed while practicing

## Quick things I learned

- The VLAN ID has to match on the other end of the link, otherwise nothing works even if your router config looks perfect.
- Put the IP on the **VLAN interface**, not on the physical port.
- A `/30` gives you only two usable addresses, so it's perfect for point-to-point links.
- Turn on **Safe Mode** when you're changing a router you're connected to remotely. It saves you if you lock yourself out.

## A note on privacy

Some IP addresses and names in the screenshots are blurred on purpose. If you do your own write-up from a real router, blur anything that belongs to a customer or an ISP before posting.

## Environment

- MikroTik RouterOS 7.x
- Configured through the web GUI (WebFig), with CLI equivalents in the PDF

## What's next

I'm planning to keep adding notes here as I learn more:

- [ ] Static routes and default gateway
- [ ] DHCP server on a VLAN
- [ ] Bridge VLAN filtering (trunk and access ports)
- [ ] NAT and basic firewall rules
- [ ] Simple queues for bandwidth limits
- [ ] OSPF / BGP basics

## Feedback

I'm still learning, so if you spot a mistake or know a better way to do something, please open an issue or a pull request. I'd appreciate it.


- GitHub: [@0diNx1](https://github.com/0diNx1)
- Portfolio: [0diNx1.github.io](https://0diNx1.github.io)
