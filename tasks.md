 **30-Day CCNA (200-301) Lab Roadmap** — one focused, hands-on lab per day, designed to build skills progressively from fundamentals to real-world integration and troubleshooting.

Each lab includes:
- 🎯 **Objective**
- ⏱️ **Estimated Time**: 45–90 mins (adjustable)
- 📦 **Topology Suggestions** (Packet Tracer, GNS3, or real gear)
- ✅ **Key Commands & Verification Steps**
- 📚 **Optional Stretch Goals** (for deeper practice)

---

### 🗓️ **CCNA 30-Day Lab Roadmap**

| Day | Lab Title | Focus Area |
|-----|-----------|------------|
| **1** | CLI Mastery & Device Initialization | Router/Switch Basics |
| **2** | IPv4 Addressing & Subnetting Practice | IP Fundamentals |
| **3** | IPv6 Addressing & EUI-64 | IPv6 Basics |
| **4** | Static & Default Routing (IPv4) | Routing Fundamentals |
| **5** | Static & Default Routing (IPv6) | IPv6 Routing |
| **6** | Basic Switching: VLANs & Access Ports | Layer 2 |
| **7** | Trunking & Native VLANs | VLANs & Trunks |
| **8** | Router-on-a-Stick (Inter-VLAN Routing) | Layer 3 Switching |
| **9** | Layer 3 Switching with SVIs | Multilayer Switching |
| **10** | OSPFv2 Single-Area (Point-to-Point & Broadcast) | Dynamic Routing (IPv4) |
| **11** | OSPFv2 Multiaccess & DR/BDR Control | OSPF Deep Dive |
| **12** | OSPFv3 (IPv6) Single-Area | Dynamic Routing (IPv6) |
| **13** | First-Hop Redundancy: HSRP | Network Resiliency |
| **14** | Port Security & DHCP Snooping | Switch Security |
| **15** | SSH, AAA, and Management Security | Device Hardening |
| **16** | Standard & Extended IPv4 ACLs | Traffic Filtering |
| **17** | IPv6 ACLs & RA Guard (Conceptual) | IPv6 Security |
| **18** | NAT: Static, Dynamic, and PAT | Address Translation |
| **19** | DHCP Server on Router & Relay | IP Services |
| **20** | DNS, NTP, and Syslog Configuration | Network Management |
| **21** | EtherChannel (PAgP & LACP) | Link Aggregation |
| **22** | Spanning Tree Protocol (STP/RSTP) Tuning | Loop Prevention |
| **23** | Wireless: WLC + Lightweight AP (Packet Tracer) | WLAN Basics |
| **24** | QoS Basics: Classification & Marking | Network Services |
| **25** | RESTCONF/NETCONF with IOS XE (DevNet Sandbox) | Network Automation |
| **26** | Python + Netmiko: Config Backup Script | Automation (CLI) |
| **27** | Integrated Lab: Branch Office (VLANs, OSPF, NAT, ACLs) | Integration |
| **28** | Dual-Stack IPv4/IPv6 Campus Network | IPv4/IPv6 Coexistence |
| **29** | Troubleshooting Challenge #1 (Misconfigs Hidden) | Diagnostic Skills |
| **30** | Full CCNA Capstone Lab (End-to-End Enterprise) | Exam Readiness |

---

### 🔍 **Detailed Lab Descriptions**

#### 🔹 **Days 1–5: Foundations**
**Day 1: CLI Mastery & Device Initialization**  
- Erase startup-configs, reload devices.  
- Configure hostname, domain-name, enable secret, console/VTY passwords, MOTD banner.  
- Generate crypto key, enable SSH v2.  
- Save config & verify with `show running-config`.  
✅ *Stretch*: Script config via PuTTY log or automation tool.

**Day 2: IPv4 Subnetting Practice**  
- Given `172.16.0.0/16`, subnet for:  
  - 3 LANs (60, 30, 10 hosts)  
  - 2 point-to-point links  
- Document subnets (network, mask, first/last host, broadcast).  
- Assign IPs in topology & verify with `ping`.  
✅ *Stretch*: Use DHCP on one subnet.

**Day 3: IPv6 Addressing & EUI-64**  
- Configure global unicast (GUA), link-local (LLA), and loopback.  
- Use `ipv6 address 2001:db8:acad:1::/64 eui-64`.  
- Verify neighbor discovery with `show ipv6 neighbors`.  
✅ *Stretch*: Enable IPv6 unicast-routing & ping loopbacks.

**Day 4: Static & Default Routing (IPv4)**  
- 3-router chain: R1–R2–R3.  
- Use `ip route` with next-hop and exit interface.  
- Configure default route on edge routers.  
- Break a link → add floating static (AD 130).  
✅ *Stretch*: Add IPv4 CDP/LLDP for topology discovery.

**Day 5: Static & Default Routing (IPv6)**  
- Repeat Day 4, but with IPv6 (`ipv6 route`).  
- Observe lack of broadcast — use `show ipv6 route static`.  
✅ *Stretch*: Configure IPv6 CDP replacement: LLDP.

---

#### 🔹 **Days 6–9: Switching & Inter-VLAN**
**Day 6: Basic VLANs**  
- Create VLANs 10 (Sales), 20 (HR), 99 (MGMT).  
- Assign PCs to access ports.  
- Verify: `show vlan brief`, `show interfaces status`.

**Day 7: Trunking**  
- Configure 802.1Q trunk between switches.  
- Set allowed VLANs & native VLAN (e.g., VLAN 999).  
- Verify: `show interfaces trunk`, `show dtp`.

**Day 8: Router-on-a-Stick**  
- Use subinterfaces on router (Fa0/0.10, .20).  
- `encapsulation dot1Q 10`, `ip address`.  
- Test inter-VLAN ping.

**Day 9: Layer 3 Switching (SVI)**  
- Replace router with Layer 3 switch.  
- Create SVIs (`interface vlan 10`), enable IP routing.  
- Compare performance & config simplicity vs. RoaS.

---

#### 🔹 **Days 10–13: Dynamic Routing & Redundancy**
**Day 10: OSPFv2 Single-Area**  
- 4-router full-mesh or partial.  
- Use `network` statements **or** `ip ospf 1 area 0` per interface.  
- Verify neighbors, routes, cost.

**Day 11: DR/BDR & Loopback RIDs**  
- Force specific DR/BDR using `ip ospf priority`.  
- Set RID with `router-id` (use loopback).  
- Break neighbor adjacencies intentionally.

**Day 12: OSPFv3 (IPv6)**  
- Enable `ipv6 unicast-routing`, `ipv6 router ospf 1`.  
- Assign RID, enable per interface: `ipv6 ospf 1 area 0`.  
- Compare with OSPFv2.

**Day 13: HSRP**  
- Two routers, one virtual gateway (e.g., `.254`).  
- Track interface (e.g., `track 1 interface Gig0/0 line-protocol`).  
- Simulate failure → observe failover with `debug standby`.

---

#### 🔹 **Days 14–18: Security & Services**
**Day 14: Port Security & DHCP Snooping**  
- `switchport port-security`, `maximum 2`, `violation shutdown`.  
- Enable DHCP snooping: `ip dhcp snooping`, `ip dhcp snooping vlan 10,20`, `ip dhcp snooping trust` on uplinks.

**Day 15: SSH & AAA**  
- `username admin secret cisco`, `aaa new-model`, `aaa authentication login default local`.  
- Disable telnet: `transport input ssh`.  
- Generate RSA key (2048+ bits).

**Day 16: IPv4 ACLs**  
- Block HR (VLAN 20) from SSH to Sales server, but allow HTTP.  
- Apply closest to source.  
- Verify with `show access-lists counters`.

**Day 17: IPv6 ACLs**  
- `ipv6 access-list BLOCK_PING`, `deny icmp any any echo`, `permit ipv6 any any`.  
- Apply inbound on interface: `ipv6 traffic-filter BLOCK_PING in`.

**Day 18: NAT (PAT)**  
- Internal LAN → Router → “Internet” (loopback).  
- `ip nat inside/outside`, `ip nat pool`, `ip nat inside source list 1 interface Gig0/1 overload`.  
- Test web access from PC.

---

#### 🔹 **Days 19–22: IP Services & Resiliency**
**Day 19: DHCP Server**  
- Configure router as DHCP server per VLAN.  
- Exclude addresses, set default-router, DNS.  
- Use `ip helper-address` for remote subnets.

**Day 20: NTP, DNS, Syslog**  
- `ntp server 192.168.1.100`, `ip name-server 8.8.8.8`, `logging host 192.168.1.50`.  
- Generate syslog via `reload` (in lab) or `logging trap debugging`.

**Day 21: EtherChannel**  
- Bundle 2+ links between switches.  
- Try PAgP (`desirable/auto`) and LACP (`active/passive`).  
- Verify: `show etherchannel summary`.

**Day 22: STP Tuning**  
- Manipulate root bridge: `spanning-tree vlan 10 root primary`.  
- Change port cost/priority.  
- Simulate link failure → observe reconvergence.

---

#### 🔹 **Days 23–26: Wireless, QoS & Automation**
**Day 23: Wireless (Packet Tracer)**  
- Configure WLC: mgmt IP, DHCP scope, interface, AP join.  
- Create WLAN: SSID, WPA2-PSK, interface mapping.  
- Connect laptop → verify DHCP & ping.

**Day 24: QoS Basics**  
- Classify voice traffic: `class-map VOICE`, `match dscp ef`.  
- Policy-map: `priority percent 30`.  
- Apply to outbound interface.  
💡 *Note*: Simulate with traffic generators if possible.

**Day 25: RESTCONF (DevNet Sandbox)**  
- Reserve “IOS XE on CSR Latest” sandbox.  
- Use Postman:  
  - `GET /restconf/data/Cisco-IOS-XE-native:native/hostname`  
  - `GET /restconf/data/ietf-interfaces:interfaces`  
✅ *Stretch*: Modify hostname via `PUT`.

**Day 26: Netmiko Script**  
- Write Python script to:  
  - SSH into 2 routers  
  - Run `show ip int brief`, `show version`  
  - Save outputs to files  
- Use `netmiko.ConnectHandler`.

---

#### 🔹 **Days 27–30: Integration & Mastery**
**Day 27: Branch Office Lab**  
- Topology: HQ (L3 switch, server) ↔ WAN link ↔ Branch (router, 2 VLANs).  
- Configure:  
  - OSPF between sites  
  - NAT at branch  
  - ACL to block ICMP from branch to HQ server  
  - DHCP at HQ, relay at branch  
✅ Test: Branch PC → ping HQ server? Browse web?

**Day 28: Dual-Stack Campus**  
- Redo Day 27 with **both IPv4 & IPv6**.  
- Use OSPFv2 + OSPFv3, dual-stack SVIs, NAT64 optional.  
- Verify: `ping`, `ping ipv6`.

**Day 29: Troubleshooting Challenge #1**  
🎯 *Pre-broken lab*: Download or build a topology with 5 hidden issues:  
- Wrong subnet mask  
- OSPF area mismatch  
- Missing `no shutdown`  
- ACL applied in wrong direction  
- NAT inside/outside reversed  
⏱️ Time yourself — diagnose & fix all in <60 mins.

**Day 30: Capstone Lab (Full Enterprise)**  
✅ **Requirements**:  
- 2 sites (HQ + Branch)  
- 3 VLANs per site  
- OSPF (IPv4/IPv6)  
- HSRP at HQ  
- NAT/PAT at Branch  
- DHCP, DNS, NTP  
- SSH, port security, ACLs  
- Wireless SSID  
- Automation check (e.g., backup running-config)  
📌 **Success Criteria**:  
- All PCs get IPs & resolve DNS  
- End-to-end ping (IPv4 & IPv6)  
- Internet access (simulate with loopback)  
- Secure management (SSH only, no telnet)  

---

