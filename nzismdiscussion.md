# NZ ISM Azure Blueprint FAQ
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
* What are these two policies used for and why?

[Policy Setting - Enable Azure Monitor for VMs][policyenableam]
* Is this a requirement or is it optional?

[Policy Setting - Audit Diagnostic Setting][policyauditdiag]
* Audit Diagnostic Setting is a policy that applies to a lot of resources

[Policy Setting - MFA enabled for write access accounts][policymfawrite]
* MFA enabled for write access rather than role access

[Policy Setting - WAF enabled for Application Gateway][policywafenabled]
* Is the WAF required on all App Gateways?

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
[policyvmadmins]: https://github.com/BevanSin/nzismdocs/blob/master/policyvmadmins.md
[policyenableam]: https://github.com/BevanSin/nzismdocs/blob/master/policyenableam.md
[policyauditdiag]: https://github.com/BevanSin/nzismdocs/blob/master/policyauditdiag.md
[policymfawrite]: https://github.com/BevanSin/nzismdocs/blob/master/policymfawrite.md
[policywafenabled]: https://github.com/BevanSin/nzismdocs/blob/master/policywafenabled.md

<!-- External -->
[NZISM]: https://www.nzism.gcsb.govt.nz/ism-document
[AzureBP]: https://docs.microsoft.com/en-us/azure/governance/blueprints/overview
[AzureBPSamples]: https://docs.microsoft.com/en-us/azure/governance/blueprints/samples/
[NZGovDigital]: https://www.digital.govt.nz/digital-government/strategy/strategy-summary/strategy-for-a-digital-public-service/
[CID1829]: https://www.nzism.gcsb.govt.nz/ism-document#1829
[AzureArc]: https://docs.microsoft.com/en-us/azure/azure-arc/
[AZTriggerScan]: https://docs.microsoft.com/en-us/cli/azure/policy/state?view=azure-cli-latest#az_policy_state_trigger_scan