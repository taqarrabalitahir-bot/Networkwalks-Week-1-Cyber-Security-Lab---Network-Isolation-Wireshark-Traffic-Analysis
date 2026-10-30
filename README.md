# Wireshark SOC Lab: Network Infrastructure & Packet Analysis

This repository documents the completion of my practical networking and security lab environment, focused on isolating malware/attack vectors using localized subnetting and traffic analysis tools.

## 🛠️ Lab Architecture & Environment Setup
1. **Virtualization Topology:** Deployed a working cybersecurity sandbox environment within Oracle VM VirtualBox Manager featuring **Kali Linux** as the core analysis node.
2. **Network Isolation:** Engineered a dedicated **NAT Network** configured explicitly with a `10.0.0.0/24` subnet prefix, enabling complete internet simulation while safeguarding the host machine.
3. **Interface Verification:** Verified the automated DHCP address lease allocation on Kali Linux's local terminal via `ip a`, confirming routing synchronization within the `10.0.0.x` local network boundaries.

## 🕵️‍♂️ Incident Response & Packet Investigation
Utilized an enterprise Security Operations Center (SOC) framework via **Wireshark** to capture, identify, and dissect unauthorized traffic querying an organization's web infrastructure. 

### Key Investigation Metrics & Findings:
* **Total Traffic Audited:** 309 discrete network packets.
* **Malicious Footprint Identified:** Detected an anomalous block of `73` connection-initiating TCP SYN packets starting sequentially at `3.4s`.
* **Attacker Profiling:** Tracked down the exact adversarial footprint originating from Source IP `192.168.10.66` leveraging Source Port `52311`.
* **Target Mapping:** The attack target was identified as the organization's web server at Destination IP `192.168.10.20`.
* **Probing Scale:** Flagged `40` unique TCP target conversions via Wireshark's internal Conversational Statistics modules.
* **Server Vulnerability Assessment:** 
  * **Open Paths (`[SYN, ACK]`):** Ports `22` (SSH), `80` (HTTP), and `443` (HTTPS) were open and vulnerable.
  * **Closed Paths (`[RST, ACK]`):** `37` ports returned resets, actively dropping connections.
* **Final Assessment:** Verified the incident vector as an aggressive **Port Scan** reconnaissance campaign.
