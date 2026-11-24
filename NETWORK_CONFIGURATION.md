# SeaGoof Ltd v12 — Network Configuration Overview

The tables below reflect **reported configuration and observations** in the final assessment report, rather than an independent inspection of the .pkt file.

## Architecture

- Three-floor hierarchical star topology in Ulverston, UK.
- R1 (Cisco 2911) uses router-on-a-stick 802.1Q subinterfaces for inter-VLAN routing, DHCP and guest ACLs.
- One SW-CORE and eight access switches: SW-B1/B2, SW-G1/G2/G3, SW-F1/F2/F3.
- Access switches are identified as Cisco 2960 in the report. **Core-switch hardware details require reconciliation:** the equipment schedule calls it Cisco 3560, while the historical E01 `show version` record describes WS-C2960-24TT.
- The demonstrated internal multifunction DNS, HTTP, SMTP and POP3 service host uses `192.168.10.10`.

## VLANs and DHCP allocations

| VLAN | Function | Network | Gateway | Reported effective DHCP allocation | Count |
|---|---|---|---|---|---:|
| 10 | Basement Staff | 192.168.10.0/24 | 192.168.10.1 | .100–.200 | 101 |
| 20 | Ground Staff | 192.168.20.0/24 | 192.168.20.1 | .100–.200 | 101 |
| 30 | First Floor Staff | 192.168.30.0/24 | 192.168.30.1 | .100–.200 | 101 |
| 40 | Basement Guest | 192.168.40.0/24 | 192.168.40.1 | .100–.120 | 21 |
| 50 | Ground Guest | 192.168.50.0/24 | 192.168.50.1 | .100–.140 | 41 |
| 60 | First Floor Guest | 192.168.60.0/24 | 192.168.60.1 | .100–.180 | 81 |
| 99 | Management | 192.168.99.0/24 | 192.168.99.1 | Not evidenced | — |

All these subnets use mask `255.255.255.0` (/24). The report's DHCP address windows are narrower than the 254 conventional usable host addresses of each /24. Static or reserved infrastructure addresses need separate accounting.

## Client capacity planning (assumptions from the brief)

| Floor | Staff wired | Staff wireless | Guest wireless | Total connections |
|---|---:|---:|---:|---:|
| Basement | 20 | 40 | 10 | 70 |
| Ground | 30 | 30 | 30 | 90 |
| First Floor | 50 | 40 | 50 | 140 |
| **Total** | **100** | **110** | **90** | **300** |

The first-floor guest figure of 50 is a **conservative interpretation**, not an observed simultaneous count. VLAN 30's 101-lease DHCP window provides only 11 leases of headroom above its 90-connection planning baseline.

## Services and security

- Router subinterfaces: `Gi0/1.10`, `.20`, `.30`, `.40`, `.50`, `.60`, `.99`.
- Guest ACLs applied inbound: `GUEST40_IN`, `GUEST50_IN`, `GUEST60_IN`.
- Staff DHCP pools advertise DNS server `192.168.10.10`; guest pools advertise `1.1.1.1`.
- Internal DNS record: `www.seagoof.com` → `192.168.10.10`.
- Demonstrated SMTP/POP3 mail accounts: `admin@seagoof.com`, `staff01@seagoof.com`.
- Guest handsets were observed using WPA2-PSK/AES. The report records gateway reachability and blocked ICMP to selected internal destinations.
- NAT interface roles were configured, but actual external translation and ISP connectivity were **not tested**.

## Implemented versus proposed wireless architecture

The **current v12 Packet Tracer file has separate staff and guest physical access points**. This exceeds the assessment brief's *one AP per floor* requirement. The **proposal**, not a verified implemented change, is one VLAN-capable, multi-SSID enterprise AP on each of the three floors, subject to capacity and coverage assessment.

## Production considerations

Single points of failure exist at R1 and SW-CORE; combining DNS, web and mail on one host concentrates service risk. Proposed controls include managed administration, logging, backups, UPS and stronger wireless authentication. These are recommendations, not claims of fully deployed controls.

## Educational use

Any demonstration credentials in the simulated project are not suitable for use in real production environments.

_Source: SeaGoof_Ltd_v12_1.docx, Sections 1–7, Appendix D and Appendix C._
