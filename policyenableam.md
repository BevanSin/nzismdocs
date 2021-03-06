# Policy Setting - Enable Azure Monitor for VMs
![banner]

<br/>

This is a single policy setting that requires a parameter when deploying the Policy Initiative and is not optional.  The parameter allows the policy to determine that the Virtual Machines are logging their events to a core logging platform for centralised analysis. 

**Enable Azure Monitor for VMs**

Enable Azure Monitor for the virtual machines (VMs) in the specified scope (management group, subscription or resource group). Takes Log Analytics workspace as parameter.

**Information Security Manual**

This policy setting links to [16.6.8 System User Identification CID 2006][CID2006].

*Agencies MUST develop and document logging requirements covering:*

* *the logging facility, including:*
* *log server availability requirements; and*
* *the reliable delivery of log information to the log server;*
* *the list of events associated with a system or software component to be logged; and
event log protection and archival requirements.*

## Explanation

Having comprehensive information on the operations of a system can assist system administration, support information security and assist incident investigation and management.  In some cases forensic investigations will rely on the integrity, continuity and coverage of system logs.

Alongside this, several of the other policy settings also require that logging is enabled, and some management services in Azure require more in depth logging to be able to predict issues, or alert for maintenance such as patching.

To that end, a centralized logging mechanism using Log Analytics is recommended to ensure that events are collected and triage is performed.

However, some agencies maintain their own log capture and management systems, so this requirement for Virtual Machine logging is not required.  If this is the case, then this an [exemption][AzurePolicyExempt] can be implemented with an explanation to ensure it is captured for reporting purposes.

## Reference Links
* [New Zealand ISM][NZISM]
* [New Zealand Strategy for a Digital Public Service][NZGovDigital]
* [Azure Blueprints Documentation][AzureBP]
* [Azure Blueprint Samples][AzureBPSamples]

<!-- Local -->
[Banner]: images/banner.png

<!-- External -->
[NZISM]: https://www.nzism.gcsb.govt.nz/ism-document
[AzureBP]: https://docs.microsoft.com/en-us/azure/governance/blueprints/overview
[AzureBPSamples]: https://docs.microsoft.com/en-us/azure/governance/blueprints/samples/
[NZGovDigital]: https://www.digital.govt.nz/digital-government/strategy/strategy-summary/strategy-for-a-digital-public-service/
[CID1829]: https://www.nzism.gcsb.govt.nz/ism-document#1829
[CID2006]: https://www.nzism.gcsb.govt.nz/ism-document#2006
[AzureArc]: https://docs.microsoft.com/en-us/azure/azure-arc/
[AzurePolicyExempt]: https://docs.microsoft.com/en-us/azure/governance/policy/concepts/exemption-structure