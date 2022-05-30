# New Zealand ISM Restricted Azure Policy Initiative v3.5
![banner]

<br/>

## Update 01 June 2022
The latest update for the NZISM Policy Initiative is now live to bring it up to date with the version of the New Zealand Information Security Manual v3.5 which was published earlier this year.  This update introduces a series of changes and updates due to feedback from the community, changes to the underlying platform and changes to the services in Azure.  As ever, always evolving and updating!

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

The underlying technology for managing the initiative has also moved forward.  The Blueprint that this Policy Initiative originally was deployed alongside is being deprecated as the Azure Blueprint service changes path.  Like all Azure services, this is due to the usage patterns of the people who consume Azure services, requests from the community and innovation from the Microsoft engineering team.  When we deployed the NZISM initiative in the past, the blueprint was not used as most companies manage their subscriptions and environments in different ways.  As this is not used, we dropped it from the NZISM scope as it seemed to add no benefit.  Also, as the Defender for Azure capability evolved, more focus was put on integrating with that console as it was the main dashboard that compliance staff interacted with the output for the initiative.

One of the challenges in the community was how to know which version of the NZ ISM you were being compliant with.  The version of the initiative and the NZISM are not linked, so while the NZISM is not at v3.5 as of June 2022, the Policy Initiative is on v9.0.  To remedy this, we changed the name to include the version number to make that more clear.  So the new release will be called New Zealand ISM Restricted v3.5.

Another issue is change control - by default, many organisations simply deployed the NZ ISM Initiative directly from the gallery into their tenant. While this will still acheive the outcome of applying the initiative to the customer tenant, the issue is that it is the object that was published by Microsoft.  So when Microsoft update that initiative due to policy deprecation, response to a bug or change in policy feature, the initiative the customer has deployed will be automatically updated as well.  Most of the time this is not an issue, but it does raise the issue of change control, and good policy management in Azure.  From a change control perspective, the customer loses the ability to know exactly when change is occuring, so if an issue does arise it may take some time to track down the root cause.  And good policy management means that you deploy policy to test areas first to ensure that changes will not cause a problem, before deploying to the wider environment.
To address this it is recommended that the initiative is copied, and then deployed as per the instructions in this document.  This ensures that a unique resource is created in the customer tenant, and updates can be deployed following the change control process established by the customer.

## What is a Policy Initiative?
Azure Policy evaluates resources in Azure by comparing the properties of those resources to business rules. These business rules, described in JSON format, are known as policy definitions. To simplify management, several business rules can be grouped together to form a [policy initiative][AzurePolicyInit]. Once your business rules have been formed, the policy definition or initiative is assigned to any scope of resources that Azure supports, such as management groups, subscriptions, resource groups, or individual resources. The assignment applies to all resources within the Resource Manager scope of that assignment. Subscopes can be excluded, if necessary. For more information, see [Scope in Azure Policy][AzurePolicyScope].

Multiple policies can be deployed against the same subscriptions.  Agencies that must adhere to government regulation, industry regulation and their own internal policies can layer them to ensure that they adhere to all.  You can also disable enforcement on some, to ensure that you are reporting on compliance only and reducing the complexity of layers of enforcement.  [Planning policy layering][AzurePolEvaluate] in this way requires some thought and design to ensure there is no policy collision but a simple way to manage it is to use naming conventions on the policy objects to identify which ones you are enforcing and which ones you are not.  Disabling enforcement mode is also a good way of testing the impact of new settings.

If you are also training your engineers to understand DevOps workflows, managing policy via code repository is a good way of starting them on that journey.  You can manage your Policy templates as code in a repo of your choice, and deploy it directly [to Azure using a DevOps pipeline][AzurePolascode].

<img src="images/management.png" alt="Management" title="Management" width="50%" />

<br/>
<br/>

All Azure Policy data and objects are encrypted at rest. For more information, see [Azure data encryption at rest][AzureDataRest].

## How to deploy the NZ ISM Restricted Policy Initiative

When deploying the Policy initiative, the key thing to rememeber is that you need to create a resource based on the gallery item, not use the gallery item directly.  This is to make sure that the object you deploy to your tenant is a unique object.  That way, when Microsoft updates the policy initiative, your copy is unaffected - you own the change and update process, and you can use your policy update and release process to check the new version wont have any impact on the resources in your tenant.  Of course, this means you need to *have* a change and release process for policy, and someone responsible for monitoring the updates to the initiative.  But this is part of good governance of a cloud environment as laid out in the [Cloud Adoption Framework][CAF-GOV]

1. Select All services in the left pane. Search for and select Policy.
2. Click on Definitions
3. In the Search field type New Zealand and the New Zealand ISM Restricted policy should be listed
4. Click the ellipsis at the end of the line and select Assign
5. Set the scope by selecting the Subscription this policy will apply to - alternatively you can apply it to a Management group to ensure it applies to all subscriptions
> Note: The Policy Enforcement switch here allows you to disable any Enforcement policies and only return compliance if required.  At the time of writing all explicit deny policies had been removed from this template as it is primarily designed to report on compliance, and not enforce, a specific security template.  This is also a good way of testing the impact of new policies.
6. Click Parameters.  There should be no parameters to configure with v3.5 but if there are due to future changes, you will be prompted to put entries in for those parameters here. 
7. Click Review and Create.  Notice on this last screen the specific settings that require input are listed here in the Parameters section along with your entries.  Its a good way to ensure you have configured the correct parameters if they are required.
8. Click Create.

## How to measure compliance

Once the policy has deployed it takes some time to review all the resources and assess compliance.  Once complete, you can review this in the core Policy screen

<img src="images/policy.png" alt="Policy" title="Policy" width="50%" />

On the overview screen, click on the NZ ISM Policy to open the Initiative Compliance dashboard

<img src="images/policy1.png" alt="Policy" title="Policy" width="50%" />

You should see an overview of compliance, with the non-compliant controls listed below.  If you click on one of the non-compliant controls it will take you to a detail screen explaining the NZ ISM control that is non-compliant (with a link to read more).  If you click on Policies it will show the Azure Policies that are linked to this control, and which ones are not compliant.  If you click on Resource Compliance this shows the specific resources that are not meeting the required policy.

## How to remediate

Some policies have automated remediation tasks you can kick off from the Policy console.  From the Initiative Compliance dashboard, click on Create Remediation Task at the top of the screen.
In the drop down box this will list the specific policies you can Remediate (e.g. Deploy Dependency agent for Windows virtual machines)
It will also list the Resources this remediation task will apply to, so when you click Remediate it will initiate the task on all of those resources.  In the screenshot below, this is an example of deploying the dependency agent for a non-compliant Windows machine.

<img src="images/remediation.png" alt="Policy" title="Policy" width="50%" />

## How to override

For some environments or resources, some policies or configurations may not be valid or required.  Examples of this might be where you are achieving compliance through a different method like monitoring VM resources through the use of a 3rd party security system.  If thats the case, you can override the specific control permanently or for a defined term with an explanation.  This ensure the override process is auditable and reportable.

From the Initiative Compliance dashboard, click on Create Exemption Task at the top of the screen
This walks you through a series of screens to configure the category and expiration of the Exemption, and the specific scope and policies that this exemption covers.

## How to keep up to date

As feedback is received from the community, and as new policy settings are developed and the NZ ISM evolves to address new threats, so will the sample template change.  To keep up to date, you can simply redeploy the new version of the Policy Initiative in the same way that you have previously deployed it, and remove the old version.  As discussed earlier, policy deployment and staying current with updates in Azure is a muscle that needs to be built as part of a good Cloud Ops team, so the NZ ISM is a good artefact to use to train that muscle.

![AzurePolicyWorkflow]

Using Azure DevOps to check in the code, version it and deploy it to Azure is an automated and auditable process that is highly recommended to streamline this process.

## Microsoft Defender for Cloud and exporting a report

The NZ ISM Policy Inititiative is now available as a built in compliance report in the Microsoft Defender for Cloud dashboard.

<img src="images/securitydashboard.png" alt="Policy" title="Policy" width="50%" />

You can view your compliance as a more detailed dashboard, and also export this as a PDF or CSV.

[See here for more information on how this works][DfCRegComp].

## Feedback
An important aspect of this policy initiative is to establish a feedback loop between the government agencies, the policy creators and the technology partners.  Working together as a community will ensure that as our technology evolves, so does the governance and management strategy.  It also means that all participants can leverage the shared learnings from establishment through to consumption.

We welcome feedback on things that can improve the artifact's we have published.  Microsoft will be working with the NZ Government to continue to update the Policy Initiative in future to ensure the Azure gallery items stay in step with the standards published by the NZ government.

To that end, for all feedback or questions on the NZ ISM Restricted Policy Initiative, please feel free to contact me at bevan.sinclair@microsoft.com, or simply talk to your Microsoft account team who can assist.  For feedback on the NZ ISM Restricted standard itself please send all requests to nzism@gcsb.govt.nz.

Any items that merit more discussion, or we identify as items that the community would benefit with more in depth understanding can be found in the other markdown document [NZ ISM Discussion][NZISMDiscussion]

## Thanks to
This work has been and continues to be a team effort so thanks to the staff at the New Zealand GCSB and NCSC, the agencies who gave their time to pilot the policies, and the internal Microsoft team.  Together we are all working towards setting a great baseline of security for all of New Zealand in the (long white) Cloud.  Also thanks to the Linked In community who have proffered valuable insights and shared the content (@davidwhitenz at Theta!).

## Reference Links
* [New Zealand ISM][NZISM]
* [New Zealand Strategy for a Digital Public Service][NZGovDigital]


<!-- Local -->
[Banner]: images/banner-w.png
[Blueprint]: images/blueprint.png
[Management]: images/management.png
[Dashboard]: images/securitydashboard.png

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
[DfCRegComp]: https://docs.microsoft.com/en-us/azure/defender-for-cloud/regulatory-compliance-dashboard
[AzurePolicyWorkflow]: https://docs.microsoft.com/en-us/azure/governance/policy/media/policy-as-code/policy-as-code-workflow.png
[NZISMDiscussion]: https://github.com/BevanSin/nzismdocs/blob/master/nzismdiscussion.md
[CAF-GOV]: https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/govern/guides/standard/security-baseline-improvement
[isanz]: https://www.isanz.org.nz/#entries