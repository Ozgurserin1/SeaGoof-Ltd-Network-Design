# SeaGoof Ltd v12 — Troubleshooting and Corrective Actions

This table describes the historical symptoms and corrective actions recorded in **Appendix C** of the final report. It is a record of troubleshooting, not a claim of newly executed tests.

| Issue | Symptom | Corrective action | Evidence | Outcome / limitation |
|---|---|---|---|---|
| DHCP conflicts / duplicate leasing | Router conflicts and unusual DHCP binding/ARP records | Disabled the server's additional DHCP service, reviewed R1 scopes and conflict outputs | E30, E33–E42, E67, E75, E120 | Final conflict register empty; root cause of every historical entry not independently proven |
| Basement client DHCP | B-PC01 initially lacked correct gateway and DNS settings | Inspected DHCP settings and renewed client lease | E38–E43 | Gateway and lease subsequently verified |
| First Floor VLAN/STP | SW-F2/F3 initially lacked VLAN 30 active instance | Created VLAN 30; checked trunk, STP, and saved configuration | E76–E77 | Inspected uplinks forwarded; other links not exhaustively tested |
| Transient First Floor ping loss | Initial server ping succeeded 3/4 | Retested after learning/convergence interval | E80, E80-B | 4/4 on repeat; ARP explanation plausible, not proven |
| Missing DNS A record | www.seagoof.com initially produced NXDOMAIN | Added DNS A record pointing to 192.168.10.10 | E81–E84 | Later DNS lookup passed |
| Default HTTP page | Packet Tracer's default web page appeared | Replaced/updated index.html | E85–E89 | Custom SeaGoof homepage displayed |
| Email setup | Domain and accounts initially missing | Configured seagoof.com and admin/staff01 email clients | E90–E99 | Bidirectional send/receive verified |
| Guest isolation | Guests should reach their gateway but not internal employee/server networks | Applied inbound guest ACLs; inspected tests | E107–E119 | ICMP checks passed for three representative guest phones |

## Verification boundary

An earlier failure should not be relabelled as an original PASS. Follow-up test evidence supports only the later recorded conditions. Live ISP access, all-protocol guest isolation, the final root cause of all DHCP warnings and complete production resilience were not verified.

_Source: SeaGoof_Ltd_v12_1.docx, Appendix C._
