## 3.1 Architecture Models
 
> IaaS correction: Your notes defined IaaS as "Information as a Service." The correct definition is Infrastructure as a Service. IaaS provides compute, storage, and networking. The customer manages the OS, applications, and data. This is a common exam question.
 
### Cloud Service Models and Shared Responsibility
 
| Model | Definition and Customer Responsibility |
|---|---|
| IaaS | Infrastructure as a Service. Provider supplies compute, storage, and networking. Customer manages OS, applications, and data. Highest customer responsibility. |
| PaaS | Platform as a Service. Provider supplies infrastructure and OS. Customer manages applications and data. Examples: Azure App Service, Google App Engine. |
| SaaS | Software as a Service. Provider manages everything. Customer manages data and user access only. Examples: Microsoft 365, Salesforce. |
 
Shared responsibility shifts based on the service model:
 
1. IaaS: customer owns OS through data. Provider owns physical hardware through hypervisor.
2. PaaS: customer owns applications and data. Provider adds OS and runtime management.
3. SaaS: customer owns data and user access only. Provider manages everything else.
### Architecture and Infrastructure Concepts
 
| Concept | Description |
|---|---|
| IaC | Infrastructure as Code. Servers, networks, and apps defined as version-controlled code. Repeatable and auditable. Misconfiguration in a template deploys at scale across all instances. |
| Serverless | Function as a Service (FaaS). Stateless compute containers. Event-triggered and ephemeral. Scaled and managed by the cloud provider. Developer writes logic only. |
| Microservices | Application broken into independent services communicating via APIs. Outages contained to individual services. Each component scales independently. |
| Containerization | Packages code and dependencies into a portable unit. Shares the host OS kernel. Isolated from other containers. Lighter and faster than VMs. Less isolation than VMs. |
| Virtualization | Multiple OSs on shared hardware via a hypervisor. Each VM has its own OS. Stronger isolation than containers. Higher overhead and cost. |
| IoT | Sensors, smart devices, wearables, facility automation. Weak default credentials, limited patching, no endpoint agent support. |
| ICS/SCADA | Industrial Control Systems and Supervisory Control and Data Acquisition. Manages physical industrial processes. Must be air-gapped or strictly segmented. Availability is the primary security concern. |
| RTOS | Real-Time Operating System. Processes events within strict time constraints. Industrial equipment, vehicles, military. Difficult to patch. Availability is critical. |
| Embedded Systems | Fixed-function hardware and software. Optimized for size and cost. Traffic lights, medical imaging, digital watches. Often cannot be patched by end users. |
| High Availability | System designed to remain continuously operational. Redundant components, clustering, and failover. Higher cost. Reduces MTTR. |
 
### Container vs. VM Isolation
 
```
Container:
- Shares the host OS kernel with all containers on that host
- A kernel exploit may affect all containers on that host
- Lighter weight, faster startup, lower cost
 
VM:
- Each VM runs its own OS on a hypervisor
- A VM exploit is isolated to that VM by hardware-level hypervisor separation
- Stronger isolation, higher overhead, higher cost
 
Use containers when performance and density are the priority.
Use VMs when strong workload isolation is the priority.
```
 
### Network Infrastructure
 
| Concept | Description |
|---|---|
| Physical Isolation | Devices physically separated with no shared media. Air-gapped systems have zero network connection at all. |
| VLAN | Virtual Local Area Network. Logical segmentation on the same physical switch. Traffic cannot cross VLAN boundaries without a Layer 3 device. |
| SDN | Software-Defined Networking. Separates data plane (forwarding), control plane (routing decisions), and management plane (configuration) into distinct functional layers. |
| DMZ / Screened Subnet | Zone between the internet and the internal network. Hosts public-facing services (web, email, DNS). Internal systems are never directly reachable from the internet. |
 
### DMZ Traffic Flow Rules
 
```
Permitted:  internet > DMZ (specific public-facing services only)
Permitted:  DMZ > internal (restricted and inspected)
Never:      internet > internal (direct access to internal systems)
```
 
The DMZ absorbs attacks targeting public services without exposing the internal network.
 
### On-Premises vs. Cloud vs. Hybrid
 
- On-premises: full control of security posture, customizable, on-site IT manages uptime. Security changes require procurement and configuration time.
- Cloud-based: centralized security managed by provider, lower upfront cost, 3rd party handles physical and infrastructure security. Data travels over public internet.
- Hybrid: mix of both. Primary risks: network protection mismatches, different monitoring approaches, data leakage across the public internet.
### Infrastructure Considerations
 
| Consideration | Description |
|---|---|
| Availability | System uptime required for users to access data and complete transactions. |
| Resilience | Ability to maintain availability and recover from failure. Measured by MTTR. |
| Cost | Installation, ongoing maintenance, replacement. Operating vs. capital expense classification. |
| Responsiveness | Time from request to response. Sensitivity to delays drives architecture choices. |
| Scalability | Speed of capacity increase or decrease. Security monitoring must scale with the system. |
| Ease of Deployment | Complexity of provisioning. Orchestration and automation reduce risk of missed steps. |
| Risk Transference | Cybersecurity insurance. Covers attacks, downtime, ransomware, business interruption, and legal liability. |
| Ease of Recovery | Time and complexity to restore from failure. Critical design consideration. |
| Patch Availability | Regularity of vendor-issued security updates. Some vendors rarely patch. |
| Inability to Patch | Embedded systems, HVAC, time clocks often cannot be updated by end users. Requires compensating controls such as a dedicated firewall or IPS signatures. |
| Power | Primary power, UPS (short-term), generators (long-term). Data center power requires extensive engineering. |
| Compute | Cloud offers elastic compute. On-premises limited to installed hardware. Multi-cloud adds complexity and geographic distribution. |
