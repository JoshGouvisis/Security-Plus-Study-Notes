## 3.4 Resilience and Recovery
 
### High Availability
 
- Load balancing: distributes traffic across multiple servers. Adds or removes servers dynamically. Provides fault tolerance and SSL offload. Servers can run different OSs.
- Server clustering: two or more servers combined into one logical unit. All nodes run the same OS. Increases capacity and availability.
### Site Resiliency
 
| Site Type | Description |
|---|---|
| Hot Site | Fully operational replica. Hardware installed, software current, data synchronized. Immediate failover. Highest cost. |
| Warm Site | Partially equipped. Some hardware pre-staged. Data and configuration must be loaded. Operational within hours to days. Moderate cost. |
| Cold Site | Empty facility with power and connectivity only. No hardware, no data, no staff. Lowest cost. Longest recovery time. |
 
Geographic dispersion is required for all site types. The recovery site must be far enough that a regional disaster does not affect both sites simultaneously.
 
### Recovery Metrics
 
| Metric | Definition |
|---|---|
| RTO | Recovery Time Objective. Maximum acceptable time to restore a system or service after failure. Set by the business based on operational impact. |
| RPO | Recovery Point Objective. Maximum acceptable data loss measured in time. Defines how old restored data can be, which drives backup frequency requirements. |
| MTTR | Mean Time to Repair. Average time to restore a failed system. Measures actual recovery speed. Lower = more resilient. |
| MTBF | Mean Time Between Failures. Average time between system failures. Measures reliability. Higher = more reliable. |
 
```
RTO:  how quickly must you recover?          (business target, set before an incident)
RPO:  how much data can you afford to lose?  (business target, drives backup strategy)
MTTR: how long does repair actually take?    (operational measurement from actual incidents)
MTBF: how often does the system fail?        (operational measurement from operational history)
```
 
### Platform Diversity and Multi-Cloud
 
- Platform diversity: different OSs and applications limit the blast radius of OS-specific vulnerabilities.
- Multi-cloud: distributing across AWS, Azure, and Google Cloud. A breach or outage with one provider does not affect others.
- COOP (Continuity of Operations Planning): documented manual procedures for operating without computer systems. Must be tested before a disaster occurs.
### Recovery Testing
 
| Test Type | Description |
|---|---|
| Tabletop Exercise | Discussion-based. Key stakeholders walk through a simulated scenario verbally. No live systems. Identifies gaps in plans and communication. |
| Fail Over Test | Physically switches operations to the redundant system. Validates automatic failover within the required RTO. |
| Simulation | Tests response to a simulated event (phishing campaign, breach). Tests both technical controls and human behavior. |
| Parallel Processing | Runs primary and recovery systems simultaneously. Validates recovery without taking down the primary. |
 
### Backup Types
 
| Type | Description |
|---|---|
| Full | Complete backup of all selected data. Longest to create. Fastest to restore. Baseline for all other backup types. |
| Incremental | Backs up only data changed since the last backup of any type. Fastest to create. Slowest to restore (requires full plus all incrementals in sequence). |
| Differential | Backs up all data changed since the last full backup. Moderate creation time. Moderate restore time (requires full plus latest differential only). |
| Snapshot | Point-in-time capture of system state. Common in VMs and cloud. Contains only changes between snapshots. Fast to create and revert. |
| Replication | Continuous real-time synchronization to another location. Always-current copy. Can replicate corruption if not monitored. |
| Journaling | Log of pending write operations. Allows recovery from a failed mid-write without full backup restoration. |
 
```
Backup type comparison:
Full:         complete, longest to create, fastest to restore
Incremental:  fastest to create, slowest to restore (full + all incrementals in order)
Differential: moderate both ways (full + latest differential only)
 
3-2-1 Rule:   3 copies of data
              2 different media types
              1 copy stored off-site
```
 
### Power Resiliency
 
- UPS (Uninterruptible Power Supply): short-term power bridge. Types: Offline/Standby (switches on outage), Line-Interactive (adjusts voltage sags), Online/Double-Conversion (always on battery, cleanest power).
- Generators: long-term power backup. Powers the entire building or designated circuits. Battery UPS bridges the gap while the generator starts up.
---
 
## Quick Reference
 
| Concept | Key Facts |
|---|---|
| IaaS | Infrastructure as a Service. Customer manages OS, applications, and data. |
| PaaS | Platform as a Service. Customer manages applications and data. |
| SaaS | Software as a Service. Customer manages data and user access only. |
| Container vs. VM | Container: shares host OS kernel, lighter, faster. VM: own OS via hypervisor, stronger isolation. |
| DMZ / Screened subnet | Zone between internet and internal. Hosts public-facing services. Internal systems never directly reachable. |
| VLAN | Logical segmentation. Requires Layer 3 device to route between VLANs. |
| IaC risk | Misconfiguration in a template deploys at scale across all instances. |
| Fail-open vs. fail-closed | Fail-open: traffic flows on failure (availability). Fail-closed: traffic stops on failure (security). |
| Active vs. passive | Active (inline): blocks in real time (IPS). Passive (tap/SPAN): copy only, cannot block (IDS). |
| Layer 4 vs. Layer 7 | Layer 4: filters by port. Layer 7 (NGFW): inspects full application content regardless of port. |
| WAF | HTTP/HTTPS input validation. Blocks SQLi, XSS. Required by PCI DSS. |
| UTM | All-in-one: firewall, IPS, AV, URL filter, VPN, spam filter. |
| Jump server | Hardened bridge to a protected zone. Compromise is a significant breach. |
| Forward vs. reverse proxy | Forward: protects users accessing internet. Reverse: protects servers from internet traffic. |
| Split vs. full tunnel | Split: corporate traffic only through VPN, saves bandwidth. Full: all traffic through VPN, enables inspection. |
| SSL/TLS vs. IPsec VPN | SSL/TLS: remote user access, browser-based. IPsec: site-to-site, always-on. |
| SASE | Cloud-delivered security plus SD-WAN. Policies enforced regardless of user location. |
| Hot/warm/cold site | Hot: immediate failover, highest cost. Warm: hours to days, moderate cost. Cold: empty, lowest cost. |
| RTO | Maximum acceptable time to restore service. Business target. |
| RPO | Maximum acceptable data loss in time. Drives backup frequency. |
| MTTR | Average time to restore a failed system. Lower = more resilient. |
| MTBF | Average time between failures. Higher = more reliable. |
| Full backup | Complete copy. Fastest restore. |
| Incremental backup | Changes since last backup. Fastest to create. Slowest restore. |
| Differential backup | Changes since last full. Moderate both ways. |
| 3-2-1 rule | 3 copies, 2 media types, 1 off-site. |
| DLP | Monitors and blocks unauthorized data movement. Email, USB, cloud upload, print. |
| Data sovereignty | Data subject to laws of the country where it is stored. GDPR: EU citizen data must stay in EU. |
| Geofencing | Automatically allows or restricts access based on user's physical location. |
| Data at rest | Stored. Encrypt with full-disk or file-level encryption. |
| Data in transit | Network. Protect with TLS or IPsec. |
| Data in use | RAM, CPU cache. Mostly decrypted. Vulnerable to memory scraping. |
 
