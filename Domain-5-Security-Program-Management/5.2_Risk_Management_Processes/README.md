## 5.2 Risk Management
 
### Risk Identification and Assessment Types
 
- Risk identification: understand potential risks, identify weaknesses, qualify internal and external threats.
- Ad hoc assessment: performed when required for a specific situation (company acquisition, new equipment, unique threat). One-time investigation.
- Recurring assessment: at standard intervals. Quarterly internal assessments. PCI DSS requires annual assessments. Legal requirements may mandate specific frequencies.
- Continuous assessment: built into ongoing processes. Change control requires risk assessment as a standard step.
### Risk Analysis: Qualitative vs. Quantitative
 
| Method | Description |
|---|---|
| Qualitative | Descriptive risk assessment. Uses opinions and judgments. Traffic light grids (red/yellow/green). Likelihood rated as rare, possible, or almost certain. Useful when numerical data is unavailable. |
| Quantitative | Numerical risk assessment. Uses formulas and historical data. Produces monetary values for risk decisions. SLE, ALE, and ARO are quantitative tools. |
 
### Quantitative Risk Formulas
 
| Term | Definition |
|---|---|
| AV (Asset Value) | Monetary value of the asset to the organization: purchase cost, impact on sales, potential regulatory fines if compromised. |
| EF (Exposure Factor) | Percentage of asset value lost if the vulnerability is exploited. 0.25 = 25% loss. 1.0 = total loss of asset. |
| SLE (Single Loss Expectancy) | AV x EF. Monetary loss expected from a single incident. |
| ARO (Annualized Rate of Occurrence) | How many times per year the incident is expected to occur. Based on historical data or industry estimates. |
| ALE (Annualized Loss Expectancy) | SLE x ARO. Total expected annual monetary loss from a specific risk. |
 
```
Risk formula chain:
AV x EF = SLE
SLE x ARO = ALE
 
Worked example:
7 laptops stolen per year. Each laptop worth $1,000. Total loss when stolen.
AV  = $1,000
EF  = 1.0  (100% loss)
SLE = $1,000 x 1.0 = $1,000
ARO = 7
ALE = $1,000 x 7 = $7,000
 
Decision: any security control costing less than $7,000/year is financially justified.
This is the core logic of quantitative risk decision-making.
```
 
### Risk Appetite and Tolerance
 
- Risk appetite: the amount of risk an organization is willing to accept in pursuit of its objectives. Three postures: conservative (low tolerance), neutral, expansionary (willing to accept more risk for greater reward).
- Risk tolerance: the acceptable variance around the risk appetite. Usually higher than appetite. The operating range within which risk is actively managed.
### Risk Register
 
- Documents identified risks, their likelihood, impact, owner, and mitigation status.
- Key risk indicators: metrics that signal potential risk increases. Each assigned to a risk owner.
- Risk threshold: the point at which the cost of mitigation equals the value gained by mitigation.
### Risk Management Strategies
 
| Strategy | Description |
|---|---|
| Transfer | Move the financial risk to another party. Cybersecurity insurance. Contracts assigning liability to vendors. |
| Accept | Acknowledge the risk and take no action to mitigate it. Formally documented with management sign-off. Acceptable when cost of mitigation exceeds risk value. |
| Avoid | Stop the activity that creates the risk. Discontinue a vulnerable service or high-risk business process. |
| Mitigate | Reduce the likelihood or impact of the risk. Invest in security controls, patching, segmentation, or training. |
| Exemption | A security policy or regulation cannot be followed due to company size, available controls, or total assets. Requires formal approval. |
| Exception | An internal policy is not applied in a specific case due to a justified business reason. Documented with a defined review timeline. |
 
### Business Impact Analysis
 
| Metric | Definition |
|---|---|
| RTO | Recovery Time Objective. Maximum acceptable time to restore a system or service after a failure. Set by the business based on operational impact. |
| RPO | Recovery Point Objective. Maximum acceptable data loss measured in time. Defines backup frequency requirements. |
| MTTR | Mean Time to Repair. Average time to restore a failed system. Measures actual recovery speed. |
| MTBF | Mean Time Between Failures. Average time between system failures. Measures reliability. Higher = more reliable. |
 
Impact categories: life (highest priority), property, safety, finance. Business impact can exceed monetary value through reputational damage, regulatory fines, and customer trust erosion.
