## 3.2 Applying Security Principles
 
### Security Zones
 
| Zone | Purpose and Trust Level |
|---|---|
| Trusted (Internal) | Corporate network. Highest trust. Users, servers, and workstations. |
| Untrusted (External) | The internet. Zero implicit trust. All traffic treated as potentially hostile. |
| DMZ / Screened Subnet | Between internet and internal. Hosts public-facing services. Internal systems not directly reachable. |
| Guest / Visitor | Isolated from corporate resources. Internet access only. Prevents lateral movement. |
| VPN Zone | Authenticated remote users. Trust level determined by policy. |
| Database Zone | Isolated segment for database servers. Accessible only from application servers. |
 
### Attack Surface
 
The attack surface is the total set of entry points an attacker can use: open ports, application code, authentication interfaces, physical access points, and human error.
 
Minimize by:
1. Closing every port not explicitly required
2. Auditing and hardening application code
3. Requiring MFA on all authentication interfaces
4. Monitoring traffic in real time
5. Removing unused software and services
### Failure Modes
 
| Mode | Behavior | Trade-off |
|---|---|---|
| Fail-open | Traffic flows on failure | Maintains availability. Creates security gap during failure. |
| Fail-closed | Traffic stops on failure | Maintains security. Causes availability impact during failure. |
 
### Active vs. Passive Monitoring
 
| Mode | How It Works | Use Case |
|---|---|---|
| Active (inline) | Device in the traffic path. Can block in real time. Device failure can impact traffic flow. | IPS (Intrusion Prevention System) |
| Passive (tap/SPAN) | Receives a copy of traffic via SPAN port or network tap. Cannot block. No traffic impact on failure. | IDS (Intrusion Detection System) |
 
### Firewall Types
 
| Type | Description |
|---|---|
| Layer 4 (Traditional) | Filters by TCP/UDP port number. Fast. Cannot inspect application content. Cannot distinguish application intent on shared ports. |
| Layer 7 (NGFW) | Inspects full application-layer content in every packet. Identifies applications regardless of port. Applies vulnerability signatures. URL categorization and content filtering. |
| WAF | Web Application Firewall. Applies rules to HTTP/HTTPS traffic. Blocks SQLi, XSS, and other web application attacks. Required for PCI DSS compliance. |
| UTM | Unified Threat Management. Combines firewall, IPS, antivirus, URL filtering, VPN, and spam filter in one appliance. Common in smaller environments. |
 
Layer 4 vs. Layer 7 decision:
- Layer 4: sufficient when filtering by specific port numbers meets the requirement
- Layer 7 (NGFW): required when you need to block or control specific applications regardless of port, or when deep packet inspection and content filtering are needed
### Network Appliances
 
- Jump server: hardened device bridging access to a protected zone. SSH, RDP, or VPN access. A compromise of the jump server is a significant breach because it bridges trust zones.
- Forward proxy: sits between users and the internet. Controls and filters outbound user traffic.
- Reverse proxy: sits between the internet and internal servers. Protects servers from direct internet access. Handles SSL offload.
- Open proxy: third-party, uncontrolled. A security risk because it is managed by an unknown party.
- Load balancer: distributes traffic across multiple servers. Active/active: all servers share load. Active/passive: standby servers activate on failure. Provides fault tolerance and SSL offload.
- Sensors and collectors: aggregate logs from IPS, firewalls, authentication systems, and web servers. Feed into SIEM for correlation, alerting, and archiving.
### Port Security: 802.1X and EAP
 
- 802.1X: IEEE standard for port-based Network Access Control. No network access is granted until the device authenticates. Works with EAP and a RADIUS/LDAP/TACACS+ authentication backend.
- EAP: Extensible Authentication Protocol. The framework used within 802.1X. Supports certificates, tokens, and passwords via RFC-defined subtypes. Prevents access until authenticated.
### Secure Communications
 
| Method | Description |
|---|---|
| SSL/TLS VPN | Remote user access. Browser or VPN client. Works through most firewalls and NAT. No pre-shared keys required on the client. |
| IPsec VPN | Site-to-site. Always-on. Firewalls act as VPN concentrators. Encrypts at the network layer. |
| Split Tunnel | Only corporate-destined traffic routes through the VPN. Internet traffic goes directly out. Saves bandwidth. Internet traffic is not inspected by corporate tools. |
| Full Tunnel | All traffic routes through the VPN. Organization can inspect and filter everything. Higher bandwidth use. |
| SD-WAN | Cloud applications communicate directly to the cloud rather than backhauling through corporate infrastructure. Reduces latency. Does not inherently address security. |
| SASE | Combines SD-WAN with cloud-delivered security. Policies enforced in the cloud regardless of user location. Next-generation VPN model. |
 
### Split Tunnel vs. Full Tunnel
 
```
Split tunnel:
- Corporate traffic through VPN
- Internet traffic goes directly out
- Saves bandwidth, improves performance
- Risk: internet traffic uninspected by corporate security tools
 
Full tunnel:
- All traffic through VPN
- Organization can inspect and filter everything
- Risk: VPN becomes a bottleneck, performance impact for remote users
 
Choose split when bandwidth and performance are the priority.
Choose full when traffic inspection and security visibility are the priority.
```
 
### Selection of Effective Controls
 
- NGFW: when application-layer inspection and control is required
- WAF: when HTTP/HTTPS input validation and web application attack prevention is the concern
- IPS (inline, active): when real-time traffic blocking is required
- IDS (passive, tap): when traffic analysis without blocking is acceptable
- SASE: when users are cloud-distributed and perimeter-based security is insufficient
- UTM: when a single integrated appliance is preferred for a smaller environment
