# Project 00: Contoso Ltd. Enterprise Virtual Lab Architecture

## 1. Objective
Designed and deployed a multi-tier virtualized enterprise lab environment simulating Contoso Ltd. (Contoso Ltd. (also known as Contoso and Contoso University) is a fictional company used by Microsoft as an example company and domain.) (edge firewall, Windows Server infrastructure, Windows 11 client endpoint, and Linux server) using VMware Workstation Pro and an isolated Layer 2 virtual switch (`VMnet2`).

## 2. Network Topology & IP Plan
- **WAN Upstream:** VMware NAT (`VMnet1`)
- **Internal LAN Switch:** Isolated Host-Only Switch (`VMnet2` - `10.20.30.0/24`, local VMware DHCP disabled)
- **FW-RTR-01 (pfSense CE):** WAN `DHCP`, LAN `10.20.30.1/24`
- **DC-SRV-01 (Windows Server 2022):** `10.20.30.10/24`, GW `10.20.30.1`
- **LNX-SRV-01 (Ubuntu 24.04):** `10.20.30.20/24`, GW `10.20.30.1`
- **WIN-CL-01 (Windows 11 Pro/Ent Linked Clone):** `10.20.30.100/24`, GW `10.20.30.1`

## 3. Key Commands Used
-Configured Windows endpoints via PowerShell (`New-NetIPAddress`, `Set-DnsClientServerAddress`, `Enable-NetFirewallRule`).
-Verified end-to-end ICMP connectivity (`ipconfig`, `ping 10.20.30.1`, `ping 8.8.8.8`).

## 4. Required Screenshots to Capture & Attach
- [ ] `01_Virtual_Network_Editor_VMnet2.png` (Showing `VMnet2` set to `10.20.30.0/24` with local DHCP unchecked)
- [ ] `02_pfSense_Console_Interfaces.png` (Showing WAN DHCP and LAN `10.20.30.1/24`)
- [ ] `03_WIN_CL_01_Ping_Verification.png` (Showing successful ping from `WIN-CL-01` to `DC-SRV-01`, `FW-RTR-01`, and `8.8.8.8`)
- [ ] `04_Snapshot_Manager_Golden_Base.png` (Showing `Golden_Base_Mod00` snapshot and Linked Clone architecture)

## 5. Findings & Lessons Learned
- Leaving VMware's built-in DHCP service enabled on a custom `VMnet` causes rogue DHCP conflicts with enterprise routers/servers.
- Using Linked Clones from a clean base snapshot reduces disk consumption by over 75% when deploying multiple test workstations.