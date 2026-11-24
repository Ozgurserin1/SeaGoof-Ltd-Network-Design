# SeaGoof Ltd v12 — Network Test Results

This file summarises the **15 key tests** recorded in Section 6, Table 5 of the v12 report. PASS refers only to the test conditions shown in the report; these tests have not been re-executed for this GitHub document.

| ID | Verification | Recorded observation | Evidence | Status |
|---|---|---|---|---|
| T01 | First Floor DHCP | F-PC01: 192.168.30.177/24, gateway .30.1, DNS 192.168.10.10 | E78 | PASS |
| T02 | First Floor gateway ping | 4/4 replies | E79 | PASS |
| T03 | First Floor server ping | Initially 3/4, retest 4/4 | E80, E80-B | PASS on retest |
| T04 | Ground Floor DHCP | G-PC01: 192.168.20.112/24, gateway .20.1, DNS 192.168.10.10 | E101 | PASS |
| T05 | Ground Floor gateway ping | 4/4 replies | E102 | PASS |
| T06 | Ground Floor server ping | 4/4 replies to 192.168.10.10 | E103 | PASS |
| T07 | Ground Floor DNS | www.seagoof.com → 192.168.10.10 | E104 | PASS |
| T08 | Ground Floor web | Custom SeaGoof page displayed | E105 | PASS |
| T09 | Bidirectional email | SMTP/POP3 send, receipt and reply | E96–E99 | PASS |
| T10 | Basement guest isolation | Internal server and staff gateway ICMP blocked, 0/4 | E108–E109 | PASS |
| T11 | Ground Floor guest isolation | Internal server and staff gateway ICMP blocked, 0/4 | E112–E113 | PASS |
| T12 | First Floor guest isolation | Internal server and staff gateway ICMP blocked, 0/4 | E116–E117 | PASS |
| T13 | Router guest ACL attachment | Inbound GUEST40_IN, GUEST50_IN, GUEST60_IN recorded | E118–E119 | PASS |
| T14 | Final DHCP conflict register | No recorded conflict entries at inspection time | E120 | PASS (register only) |
| T15 | Router startup save | Configuration save returned [OK] | E121 | PASS |

## Selected evidence files

Eleven selected screenshots are available in [evidence/](evidence/). The full report contains further historical and diagnostic screenshots not reproduced in this shortlist.

## Interpretation and limitations

- Guest-network ICMP tests are not complete proof of application-level isolation.
- An empty DHCP conflict register does not prove there are no duplicate addresses anywhere in the network.
- Successful internal DNS, web and mail tests do not demonstrate public Internet connectivity.
- The working v12 simulation does **not** satisfy the brief's one physical AP per floor constraint; a compliant three-AP production proposal is documented separately.

_Source: SeaGoof_Ltd_v12_1.docx, Section 6 and Appendices A–E._
