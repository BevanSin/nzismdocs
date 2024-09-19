# New Zealand ISM Restricted Azure Policy Initiative v3.8
![banner]

<br/>

## Update 01 September 2024
The latest update for the NZISM Policy Initiative is now live as a built-in policy initiative, to bring it up to date with the version of the New Zealand Information Security Manual v3.8 which was published in August 2024.  This update brings it back into the gallery in the Azure console, and along with the new Azure Policy Versioning feature for Built-In policies, you can now see the version of the NZISM that the policy initiative is aligned to.  This is a great step forward in ensuring that the policy initiative is kept up to date with the latest version of the NZISM, and that the community can see which version of the NZISM they are compliant with.  It also means you can deploy direct from the gallery, and you can control which version you have deployed.

## Overview
One of the challenges that government agencies have in their transition from a traditional on premises style data center to a public cloud data center is ensuring that compliance to specific security and regulatory standards is maintained.  In an on premises world the patterns for compliance are well established, and have cadences that can be controlled through defined change and assessment process.  These processes also have timelines that can wait for capability or people to be available, and wrap around technology that has a long runway for change because the agency or their service provider controls the pace of change.  In the public cloud world the pace of change is a lot faster and does not wait for any single customer to be ready, so the process for assessing compliance, and ensuring services are built in a compliant way needs to move just as quickly.

In New Zealand, our government agency responsible for establishing the guidelines is the [GCSB] (Government Communications Security Bureau) and they have established a standard that agencies must adhere to depending on the classification level of the information being stored in the platform.  They have recognized that as the government heads to a more [Digital][NZGovDigital] strategy, the standards, compliance and methods must move apace to ensure that the government can move faster while maintaining security standards.  Alongside this, the complexity and breadth of security threats is outside the capability of many agencies to respond to individually, creating a risk for all of government.

> [Digital][NZGovDigital] is about more than new technologies and improving IT systems. It also means doing things differently using new mindsets, skills, data and technologies to overcome barriers and better meet New Zealand’s needs.

Microsoft has worked with many customers and regulatory bodies to produce artifacts that enable them to work safely in public cloud environments.  These include documented processes for establishing good practice for [development][AppArch], [landing zone][LZ] design patterns, and frameworks for [Cloud Adoption][CAF].  We have also worked with government to help establish patterns to assess compliance for Azure environments, and the published those to be consumable via the Azure Portal.  Those objects are our [Azure Blueprints][AzureBP], [Azure Policies][AzurePolicy] and [Azure Policy Initiatives][AzurePolicyInit].

We also published a set of tenets to improve the quality of a workload once it has been established in Azure called the [Microsoft Azure Well-Architected Framework][WAF].  The framework consists of five pillars of architecture excellence: Cost Optimization, Operational Excellence, Performance Efficiency, Reliability, and Security.

An area that both NZ Government and Microsoft recognised that could assist New Zealand agencies and companies in cloud adoption was a translation of the NZ ISM Restricted into a set of policies that could allow the implementor a method of measuring their environment against the standard defined by the NZ ISM.  To that end, Microsoft and the GCSB worked together to establish an Azure Policy Initiative and Azure Blueprint to be published in the Azure gallery.  This allows any agency or New Zealand company to apply the standard to their Azure environment, and assess their level of compliance against a defined NZ Government standard.

The outcome of this is creating a known good baseline that every agency can adhere to, raising the base level of security across all New Zealand government.  As this is also policy as code, the process for updating and adjusting to a fast moving threat landscape becomes easier, ensuring that the risk can be reduced.  As this baseline is publicly available in the Azure gallery, New Zealand business can also adopt it, raising the bar across all of New Zealand.

## Whats changed?

This policy initiative was orginally developed in early 2021 and has been deployed in a large number of NZ tenants, both government and non-government.  This is a great sign that business and agencies are looking to the GCSB and Microsoft for guidance in security when operating in cloud environments.  The GCSB was also recognised with its partners for this work, and won the [iSANZ Best Security Project or Security Awareness Initiative award][isanz] for 2021.

The underlying technology for managing the initiative has also moved forward.  The NZISM Azure Blueprint that this Policy Initiative originally was deployed alongside has been deprecated as the Azure Blueprint service changes path.  Like all Azure services, this is due to the usage patterns of the people who consume Azure services, requests from the community and innovation from the Microsoft engineering team.  

One of the challenges in the community was how to know which version of the NZ ISM you were being compliant with.  As of June 2024, the ability to [version Built-In policies in Azure is in public preview][AzurePolicyVersioning].  This means updates such as the description, policies contained within the initiative and metadata can be tracked and clearly seen in the Azure portal.

Another issue is change control and in the past, publication through the built-in gallery, or external repos required customers to maintain copies of built-in initiatives and version them themselves.  This was a manual process and required a lot of overhead to maintain.  With the new versioning feature, the built-in initiative is now versioned by Microsoft, and the version number is visible in the Azure portal.  The description field shows the version of the NZISM the built-in is aligned to. This means you can deploy direct from the gallery and still maintain control over which version you have deployed.

[How to deploy the latest New Zealand ISM Policy Initiative?][nzismdeployment]

[What are some common questions about specific policies or the NZISM itself?][nzismdiscussion]

## Feedback
An important aspect of this policy initiative is to establish a feedback loop between the government agencies, the policy creators and the technology partners.  Working together as a community will ensure that as our technology evolves, so does the governance and management strategy.  It also means that all participants can leverage the shared learnings from establishment through to consumption.

We welcome feedback on things that can improve the artifact's we have published.  Microsoft will be working with the NZ Government to continue to update the Policy Initiative in future to ensure the Azure gallery items stay in step with the standards published by the NZ government.

To that end, for all feedback or questions on the NZ ISM Restricted Policy Initiative, please feel free to contact me at bevan.sinclair@microsoft.com, or simply talk to your Microsoft account team who can assist.  For feedback on the NZ ISM Restricted standard itself please send all requests to nzism@gcsb.govt.nz.

Any items that merit more discussion, or we identify as items that the community would benefit with more in depth understanding can be found in the other markdown document [NZ ISM Discussion][NZISMDiscussion]

## Thanks to
This work has been and continues to be a team effort so thanks to the staff at the New Zealand GCSB and NCSC, the agencies who gave their time to pilot the policies, and the internal Microsoft team.  Together we are all working towards setting a great baseline of security for all of New Zealand in the (long white) Cloud.  Also thanks to the Linked In community who have proffered valuable insights and shared the content.

## Reference Links
* [New Zealand ISM][NZISM]
* [New Zealand Strategy for a Digital Public Service][NZGovDigital]

<!-- Local -->
[Banner]: images/banner-w.png
[Blueprint]: images/blueprint.png
[Management]: images/management.png
[Dashboard]: images/securitydashboard.png
[nzismdeployment]: https://github.com/BevanSin/nzismdocs/blob/master/nzismdeployment.md
[nzismdiscussion]: https://github.com/BevanSin/nzismdocs/blob/master/nzismdiscussion.md

<!-- External -->
[NZISM]: https://www.nzism.gcsb.govt.nz/ism-document
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
[AzureDataRest]: https://docs.microsoft.com/en-us/azure/security/fundamentals/encryption-atrest
[AzureResLock]: https://docs.microsoft.com/en-us/azure/governance/blueprints/concepts/resource-locking
[AzurePolicyBuiltin]: https://docs.microsoft.com/en-us/azure/governance/policy/samples/built-in-policies
[AzurePolEvaluate]: https://docs.microsoft.com/en-us/azure/governance/policy/concepts/evaluate-impact
[AzurePolascode]: https://docs.microsoft.com/en-us/azure/governance/policy/concepts/policy-as-code
[DfCRegComp]: https://docs.microsoft.com/en-us/azure/defender-for-cloud/regulatory-compliance-dashboard
[AzurePolicyWorkflow]: https://docs.microsoft.com/en-us/azure/governance/policy/media/policy-as-code/policy-as-code-workflow.png
[NZISMDiscussion]: https://github.com/BevanSin/nzismdocs/blob/master/nzismdiscussion.md
[CAF-GOV]: https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/govern/guides/standard/security-baseline-improvement
[isanz]: https://www.isanz.org.nz/#entries
[AzurePolicyVersioning]: https://techcommunity.microsoft.com/t5/azure-governance-and-management/public-preview-announcement-azure-policy-built-in-versioning/ba-p/4186105