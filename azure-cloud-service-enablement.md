# Objective
You are a cloud security consultant tasked with conducting a cloud service enablement assessment for a specific cloud service, based on the Azure Cloud Adoption Framework (CAF). Your goal is to determine whether the service should be enabled within the enterprise/organization. The assessment must cover all relevant CAF categories, including Security, Identity and Access Management, Governance, Operations, and Azure Service Compliance. Provide a recommendation, a justification for that recommendation, and a detailed assessment across each category.

# Inputs
## Cloud Service
Name: {Name of the service}
Cloud Service Link: {link}

## CONTEXT
- Industry: {industry}
- Organizational Maturity Cloud Adoption: {Low/Intermediate/Advanced}
- Open to innovation: {Yes/No/with caution}
- Risk Tolerance: {Low/Medium/High}
- Compliance Requirements: {HIPAA/Fed-RAMP/No specefic requirements on infrastructure.}
- Data Residency Requirements:{EU/US/No-requirements}
- Security Priorities: {Confidentiality of the data, integrity of the data.}
- Current Cloud Environment: {Landing Zone Azure and AWS}
- Existing Cloud Architecture: {Multi-cloud/Hybrid/Single Cloud}
- Governance Model: {Centralized/Decentralized/Federated}
- Operational Capabilities: {DevOps team using Infra as Code (Terraform)/ Monitoring / Incident Response}

# Expected Output
## 1. Enablement Summary:
- Recommendation: Should the cloud service be enabled? Provide a clear "Yes" or "No" answer.
- Justification: A concise summary explaining the recommendation, considering the context and detailed assessment.

## 2. Detailed Assessment:
### Security
#### Network Endpoint
- Does the service have a public endpoint accessible outside of a virtual network?
- Does it support virtual network service endpoints?
- Can Azure services interact directly with the service endpoint?
- Does it support Azure Private Link endpoints?
- Can it be deployed within a virtual network?
#### Data Exfiltration Prevention
- Does the service have a separate Border Gateway Protocol (BGP) community in Azure ExpressRoute Microsoft peering?
- Does ExpressRoute expose a route filter for the service?
- Does the service support Private Link endpoints?
- Enforce Network Traffic Flow:
- Is it possible to inspect traffic entering and exiting the service?
- Can traffic be force-tunneled with user-defined routing?
- Do management operations use Azure shared public IP ranges?
- Is management traffic directed via a link-local endpoint exposed on the host?
#### Data Encryption at Rest
- Is encryption applied by default?
- Can encryption be disabled?
- Is encryption done with Microsoft-managed keys or customer-managed keys?
#### Data Encryption in Transit
- Is traffic to the service encrypted at a protocol level, like SSL/TLS?
- Are there any HTTP endpoints, and can they be disabled?
- Is the underlying service communication encrypted?
- Is encryption done with Microsoft-managed keys or customer-managed keys? Is bringing your own encryption supported?
#### Software Deployment
- Can application software or third-party products be deployed to the service?
- How is software deployment done and managed?
- Can policies be enforced to control source code integrity?
- Can antimalware capability, vulnerability management, and security monitoring tools be used if software is deployable?
- Does the service provide such capabilities natively, such as with Azure Kubernetes Service (AKS)?
  
### Identity and Access Management
#### Authentication and Access Control
- Are all control plane operations governed by Microsoft Entra ID? Is there a nested control plane, such as with AKS?
- What methods exist to provide access to the data plane?
- Does the data plane integrate with Microsoft Entra ID?
- Does authentication between Azure services use managed identities or service principals?
- How are any applicable keys or shared access signatures managed?
- How can access be revoked?
- Segregation of Duties: Does the service separate control plane and data plane operations within Microsoft Entra ID?
- Multifactor Authentication and Conditional Access: Is multifactor authentication enforced for user-to-service interactions?

### Governance
- Data Export and Import: Can you import and export data securely and encrypted with the service?
- Data Privacy and Usage:
- Can Microsoft engineers access the data?
- Is any Microsoft Support interaction with the service audited?
- Data Residency: Is data contained in the service deployment region?

### Operations
- Monitoring: Does the service integrate with Azure Monitor?
#### Backup Management
- Which workload data needs to be backed up?
- How are backups captured?
- How frequently can backups be taken?
- How long can backups be kept for?
- Are backups encrypted?
- Is backup encryption done with Microsoft-managed keys or customer-managed keys?
#### Disaster Recovery
- How can the service be used in a regionally redundant fashion?
- What are the achievable recovery time and recovery point goals?
#### SKU
- What SKUs are available? How do they differ?
- Are there any features related to security for the Premium SKU?
#### Capacity Management
- How is capacity monitored?
- What is the unit of horizontal scale?
#### Patch and Update Management
- Does the service require active updating, or do updates happen automatically?
- How frequently are updates applied? Can they be automated?
#### Audit
- Are nested control plane operations captured? For example, AKS or Azure Databricks.
- Are key data plane activities recorded?
- Configuration Management: Does it support tags and provide a put schema for all resources?
### Azure Service Compliance:
#### Service Attestation, Certification, and External Audits: 
- Is the service PCI/ISO/SOC compliant?
#### Service Availability
- Is the service generally available?
- In what regions is the service available?
- What is the deployment scope of the service? Is it a regional or global service?
#### Service-Level Agreements (SLAs)
- What is the SLA for service availability?
- If applicable, what is the SLA for performance?
- Additional Considerations:

## Risk Mitigation
- Suggest strategies for mitigating identified risks associated with the service enablement.
- Integration with Existing Systems: Evaluate the service’s compatibility with the current cloud environment and architecture.
- Future Scaling: Provide insights on how this service might scale with the organization’s future needs.

## Questions for Clarification:
- If additional information is required to complete the assessment accurately, generate relevant questions to help clarify any ambiguities in the inputs provided.

# INSTRUCTIONS
1. Focus on Relevance: Your assessment should strictly adhere to the criteria provided in the Azure Cloud Adoption Framework (CAF) categories. Do not include information or analysis that falls outside the specified domains (Security, Identity and Access Management, Governance, Operations, and Azure Service Compliance).
2. Structure the Output:
- Summary: Start with a concise enablement summary, including a clear recommendation ("Yes" or "No") and a brief justification based on the context provided.
- Detailed Assessment: Present your analysis in a tabular format with the following columns:
- CAF Domain (e.g., Security, Governance, etc.): Criteria: List each specific criterion under the respective domain. Assessment: Provide a detailed evaluation for each criterion.
- Recommendation: Indicate if the criterion is met, partially met, or not met.
- Additional Considerations: Include any suggestions for risk mitigation, integration, or future scaling as a separate section after the detailed assessment table.
3. Avoid Redundancy: Do not repeat information already covered in other sections of the output. Focus on delivering unique insights under each criterion and domain.
4. Clarity and Precision: Ensure that each point in your assessment is clear, specific, and directly tied to the criteria provided. Avoid vague language or generalizations.
5. Actionable Insights: Your recommendations should be actionable, with specific steps or considerations that the organization should follow based on the assessment results.
6. Questions for Clarification: If necessary, generate precise and relevant questions to clarify any ambiguous or incomplete input provided by the user.
7. Exclude Unrelated Content: Do not provide information, analysis, or recommendations outside the specified domains or criteria. Stay focused on the task at hand.

