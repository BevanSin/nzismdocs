# New Zealand ISM Restricted Azure Blueprint
![banner]

<br/>

## Overview

In the process of developing and deploying the blueprint, and the associated policy initiative, we have had a lot of questions and feedback.  Some of these identified technical issues or policy clarification requirements, while others simply required a more detailed explanation of the way a technology or policy worked.  This identified that there was an opportunity to share this information with the wider group to ensure that everyone benefits from the learnings or discussions with an individual agency.

To that end, we have collected all of the items that it is felt require further discussion in this document, with links to the relevant sections of NZ ISM or the Azure documentation.  This will help users of the NZ ISM Restricted Blueprint get a deeper understanding of the underlying technology or Azure Policy, Governance and Management techniques.

**DISCLAIMER** 
The information included here is supplemental to the core Azure documentation and is meant to bridge a gap between the technical documentation and implementation.  It is inferred that the technical documentation on Azure Docs is the first stop if you are looking for any information on Azure and Microsoft recommended practices.

## Overarching concepts

Just to ensure that the language used in this document is understood, there are a couple of definitions that must be stated up front.  For deeper discussions on these items please refer to the Azure Documentation portal.

* **Blueprint** - this is an Azure Service that enables cloud architects and central information technology groups to define a repeatable set of Azure resources that implements and adheres to an organization's standards, patterns, and requirements.  A blueprint consists of Policy Initiatives, Role Assignments, Resource Groups and ARM Templates
* **Policy Initiative** - Initiatives enable you to group several related policy definitions to simplify assignments and management because you work with a group as a single item.
* **Policy** - Policy definitions describe resource compliance conditions and the effect to take if a condition is met.  Effects can range from Audit (let me know when its wrong) to Deny (ensure that cannot occur).
* **Parameter** - used when applying a policy to pass further information such as boolean values (true\false) or text such as usernames and image names
* **ARM Template** - a JSON format file that describes resources to deploy and the properties for those resources

Click on the links below to view detail about a specific policy or question that has been raised.  Please let me know if theres something you need to be discussed, or should be added to the documentation.

[Policy Setting - Users included\excluded in VM Administrators Group][policyvmadmins]
* Audit Windows machines missing any of specified members in the Administrators group
* Audit Windows machines that have extra accounts in the Administrators group

[Policy Setting - Enable Azure Monitor for VMs][policyenableam]
* Enable Azure Monitor for VMs

[Policy Setting - Audit Diagnostic Setting][policyauditdiag]
* Audit Diagnostic Setting is a policy that applies to a lot of resources







## Trigger a policy Rescan
By default, audit policy is run every 24 hours to assess compliance.  If you make a change and want to see its effect straight away, you can run this by using the [az policy][AZTriggerScan] command.  

To run a refresh of all policies across the current subscription, open a Cloud Shell and type:

    az policy state trigger-scan

You can filter that by Resource Group, or target a specific subscription as well.

## Reference Links
* [New Zealand ISM][NZISM]
* [New Zealand Strategy for a Digital Public Service][NZGovDigital]
* [Azure Blueprints Documentation][AzureBP]
* [Azure Blueprint Samples][AzureBPSamples]

<!-- Local -->
[Banner]: images/banner.png
[Blueprint]: images/blueprint.png
[Management]: images/management.png
[policyvmadmins]: https://github.com/BevanSin/nzismdocs/blob/master/policyvmadmins.md
[policyenableam]: https://github.com/BevanSin/nzismdocs/blob/master/policyenableam.md
[policyauditdiag]: https://github.com/BevanSin/nzismdocs/blob/master/policyauditdiag.md

<!-- External -->
[NZISM]: https://www.nzism.gcsb.govt.nz/ism-document
[AzureBP]: https://docs.microsoft.com/en-us/azure/governance/blueprints/overview
[AzureBPSamples]: https://docs.microsoft.com/en-us/azure/governance/blueprints/samples/
[AzurePolicy]: https://docs.microsoft.com/en-us/azure/governance/policy/overview/
[AzurePolicyInit]: https://docs.microsoft.com/en-us/azure/governance/policy/overview#initiative-definition
[AzurePolicyScope]: https://docs.microsoft.com/en-us/azure/governance/policy/concepts/scope
[ARMTemplate]: https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/
[AzureRG]: https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/overview#resource-groups
[AzureRBAC]: https://docs.microsoft.com/en-us/azure/role-based-access-control/overview
[GCSB]: https://www.gcsb.govt.nz/
[NZISMPolicy]: https://docs.microsoft.com/en-us/azure/governance/policy/samples/new-zealand-ism
[NZGovCC]: https://docs.microsoft.com/en-us/compliance/regulatory/offering-nz-cc-framework-nz
[NZGovDigital]: https://www.digital.govt.nz/digital-government/strategy/strategy-summary/strategy-for-a-digital-public-service/
[WAF]: https://docs.microsoft.com/en-us/azure/architecture/framework/
[CAF]: https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/
[LZ]: https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/
[AppArch]: https://docs.microsoft.com/en-us/azure/architecture/guide/
[DavidWhite]: https://techcommunity.microsoft.com/t5/azure/azure-policy-new-zealand-information-security-manual-nzism/m-p/2144825
[AzureDataRest]: https://docs.microsoft.com/en-us/azure/security/fundamentals/encryption-atrest
[AzureResLock]: https://docs.microsoft.com/en-us/azure/governance/blueprints/concepts/resource-locking
[AzurePolicyBuiltin]: https://docs.microsoft.com/en-us/azure/governance/policy/samples/built-in-policies
[AzurePolEvaluate]: https://docs.microsoft.com/en-us/azure/governance/policy/concepts/evaluate-impact
[AzurePolascode]: https://docs.microsoft.com/en-us/azure/governance/policy/concepts/policy-as-code
[SecurityCenterRegComp]: https://docs.microsoft.com/en-us/azure/security-center/security-center-compliance-dashboard
[AzurePolicyWorkflow]: https://docs.microsoft.com/en-us/azure/governance/policy/media/policy-as-code/policy-as-code-workflow.png
[CID1829]: https://www.nzism.gcsb.govt.nz/ism-document#1829
[AzureArc]: https://docs.microsoft.com/en-us/azure/azure-arc/
[AZTriggerScan]: https://docs.microsoft.com/en-us/cli/azure/policy/state?view=azure-cli-latest#az_policy_state_trigger_scan