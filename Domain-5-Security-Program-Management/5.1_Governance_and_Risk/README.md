## 5.1 Security Governance
 
> HIPAA spelling: The correct spelling is HIPAA (Health Insurance Portability and Accountability Act), not HIPPA. Both spellings appear as answer choices on the exam. Always choose HIPAA.
 
### Policy Hierarchy
 
Understanding the distinction between these four document levels is a common exam question.
 
| Level | Definition and Example |
|---|---|
| Policy | Mandatory direction set by management. Sets the "what must be done." Example: "All data at rest must be encrypted." |
| Standard | Specific mandatory requirements that implement the policy. Sets "how much or what kind." Example: "AES-256 encryption is required for all data at rest." |
| Procedure | Step-by-step instructions for executing the standard. Sets "how to do it." Example: "To encrypt a laptop, follow these steps..." |
| Guideline | Recommended but not mandatory best practices. Sets suggested approaches. Example: "Consider using a hardware token for MFA where possible." |
 
```
Mandatory:    Policy, Standard, Procedure
Not mandatory: Guideline
 
Exam question pattern: "Which document type should be used to define the specific
encryption algorithm required by the organization?"
Answer: Standard (not policy, which would only state encryption is required)
```
 
### Security Policies
 
| Policy | Purpose |
|---|---|
| AUP | Acceptable Use Policy. Defines permitted use of company assets: internet, phones, computers, mobile devices. Limits legal liability. |
| Information Security | Centralized list of all security-related policies. Compliance requirements, detailed procedures, roles and responsibilities. |
| Business Continuity | Ensures continued operations during disruptions. Manual procedures and alternative processes. Must be documented and tested before a disaster. |
| Disaster Recovery | Comprehensive plan for restoring IT systems: recovery location, data recovery methods, application restoration, staff availability. |
| Incident Response | Defines roles, responsibilities, and step-by-step procedures for responding to security incidents. |
| SDLC | Software Development Lifecycle. Framework for taking an idea from concept to deployed application. Security integrated at each phase. |
| Change Management | Formal process: determine scope, analyze risk, create a plan, obtain end-user acceptance, present to the change control board, maintain a backout plan, document the change. |
 
### Security Standards
 
| Standard | What It Defines |
|---|---|
| Password | Complexity, length, change frequency, reset procedures, storage requirements, password manager policy. |
| Access Control | What data can be accessed, by whom, under what circumstances. Privilege documentation. Access removal procedures. |
| Physical Security | Door and building access controls. Employee vs. visitor access. Electronic locks, monitoring systems, mandatory escorts. |
| Encryption | Data encryption minimums by state (at rest, in transit, in use). Password storage methods. Approved algorithms. |
 
### Security Procedures
 
- Change management: determine scope, analyze risk, create a plan, get end-user acceptance, present to change control board, maintain a backout plan, document the change.
- Onboarding: provide employee handbook and AUP, create accounts for correct groups and departments, provision preconfigured hardware.
- Offboarding: pre-planned process for hardware disposition, data handling, account deactivation or deletion.
- Playbooks: conditional step-by-step checklists for specific scenarios (data breach, ransomware recovery). Can be manual or automated. Integrated with SOAR platforms.
- Monitoring and revision: security posture must evolve continuously. Update policies to address new threats and tighten controls as the environment changes.
### Governance Structure
 
| Structure | Description |
|---|---|
| Boards | Panel of specialists. Sets tasks and requirements for committees. Provides strategic direction. |
| Committees | Subject matter experts. Considers board input. Determines next steps and presents findings back to the board. |
| Government Entities | Legal, administrative, and political requirements. Open to public scrutiny. Regulatory oversight. |
| Centralized | Single group of decision makers in one location. Consistent, unified policies. Risk of bottleneck and single point of failure. |
| Decentralized | Decision-making distributed across individuals or locations. More flexible. Risk of inconsistent policies and standards. |
 
### Regulatory and External Considerations
 
- Regulatory: mandated logging, data storage, data protection, and retention requirements.
- Legal: reporting obligations for illegal activities, holding data for legal proceedings, breach notification laws.
- Industry-specific: electrical/utility systems require isolated controls. Medical requires encrypted storage and detailed access logs.
- Local/Regional: city and state government records, vehicle registration, medical licensing.
- National: HIPAA, COPPA (children's online privacy), federal defense requirements.
- Global: multinational companies, GDPR, varying legal jurisdictions across countries.
### Data Roles and Responsibilities
 
| Role | Responsibilities |
|---|---|
| Data Owner | Senior executive accountable for specific data. VP of Sales owns customer relationship data. Treasurer owns financial data. Defines data classification. |
| Data Controller | Manages the purpose and means of how personal data is processed. Defines what data is collected and why. |
| Data Processor | Processes data on behalf of the data controller. Often a third party. Example: a payroll company that processes employee payroll data. |
| Data Custodian/Steward | Responsible for data accuracy, privacy, and security. Assigns sensitivity labels, ensures compliance, manages access rights, implements security controls. |
