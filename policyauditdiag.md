# Policy Setting - Audit Diagnostic Setting
![banner]

<br/>

This policy relates to the Diagnostic Setting on a resource, and can apply to many resource types across the entire azure stack.  It is simply looking to ensure that the Diagnostic logging is enabled on each resource type to capture all metrics and events related to that resource.  This is important to ensure that if something is going wrong, you will have the base information to be able to diagnose the issue, or trace a security event. 

**Audit Diagnostic Setting**

Audit diagnostic setting for selected resource types

**Information Security Manual**

This policy setting links to [16.6.7 Content of System Management Logs CID 2001][CID2001].

A system management log SHOULD record the following minimum information:

* all system start-up and shutdown;
* service, application, component or system failures;
* maintenance activities;
* backup and archival activities;
* system recovery activities; and
* special or out of hours activities.

## Explanation and instructions

The challenge with this policy is that the name and description are quite high level as it is a basic configuration item across nearly all resources. Also, because it is a property of so many resources, tracking it down can be problematic, and time consuming.  To that end, here is a step by step guide for enabling it manually and by policy to help you keep on top of that particular problem.

### Whats it looking for

As you can see in the snip below the two configuration items this policy is probing is logs.enabled and metrics.enabled under Microsoft.Insights/diagnosticSettings.  These two settings 

![auditdiag]

## How do I configure it manually?

The specific setting this policy relates to is found in the Diagnostic Settings on the Azure Resource.  To alter a non-compliant resource, from the Policy dashboard click on the NZ ISM Restricted Policy, then click on the Policies column.  In there you can sort by the name, and find the Audit Diagnostic Setting policy and click on it.

![console1]

Once there click on a resource that is Non-compliant - in the example below I am selecting ra-hybrid-vpn-vnet, one of my Virtual Networks.

![console2]

This will then show the detail of the object compliance.  From there click on View Resource.

![console3]

Once you are on the resource screen click the Diagnostic settings on the left hand menu.  This is the area the policy is auditing, and it should be empty if it has triggered as non-compliant.  It may also trigger as non-compliant if it is only partially configured as the policy existence condition is "AllOf" logs and metrics equals "true".  Click on Add Diagnostic Setting.

![console4]

In the Diagnostic Setting screen, type a name in the Diagnostic Setting Name field

Select all fields under the **log** and **metric** headings

Select "Send to log analytics workspace", and from the dropdown boxes select the subscription and Log Analytics workspace the logs should be sent to.  You can also use a storage account if you consume the logs from there into another solution, or an event hub if you are [playing the events into a 3rd party solution][AzureMonEventHub].

![console5]

Once complete, click Save and the diagnostic logs will start collecting into the Log Analytics workspace.

You can trigger a policy refresh after a few minutes using the **az policy** command in the console if you want to ensure that this has made the resource compliant.

## How do I configure it automatically for all resources?

This can be accomplished using a custom policy which can make up part of your overall management and governance policy framework.  There are plenty of samples for you to review and consume from the [Microsoft public Git repository here][GitAuditDiagSetting] - I highly recommend you start with those.

The setting you should use is [DeployIfNotExists][AzurePolDeploy] to ensure that it only applies to resources not already configured.

Check the main [Microsoft documentation][AzureMonitorScale] on the steps to create a policy and deploy this at scale.  I would recommend you create and manage a policy like this using a DevOps pipeline as this is a good starting point to get traditional IT people to start deploying infrastructure and configuration as code.

The key outcomes from this would be:

* centralised management of policy
* centralised management of logging and events
* more secure management pipeline

Check [this example on how to configure policy via a devops pipeline][AzurePolDevOps] for a walkthrough.

## Reference Links
* [New Zealand ISM][NZISM]
* [New Zealand Strategy for a Digital Public Service][NZGovDigital]
* [Azure Blueprints Documentation][AzureBP]
* [Azure Blueprint Samples][AzureBPSamples]

<!-- Local -->
[Banner]: images/banner.png
[Blueprint]: images/blueprint.png
[Management]: images/management.png
[AuditDiag]: images/policyauditdiag1.png
[Console1]: images/policyauditdiag2.png
[Console2]: images/policyauditdiag3.png
[Console3]: images/policyauditdiag4.png
[Console4]: images/policyauditdiag5.png
[Console5]: images/policyauditdiag6.png

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
[CID2006]: https://www.nzism.gcsb.govt.nz/ism-document#2006
[CID2001]: https://www.nzism.gcsb.govt.nz/ism-document#2001
[AzureArc]: https://docs.microsoft.com/en-us/azure/azure-arc/
[AzurePolicyExempt]: https://docs.microsoft.com/en-us/azure/governance/policy/concepts/exemption-structure
[AzureMonEventHub]: https://docs.microsoft.com/en-us/azure/azure-monitor/essentials/stream-monitoring-data-event-hubs
[GitAuditDiagSetting]: https://github.com/Azure/azure-policy/tree/master/samples/Monitoring
[AzurePolDeploy]: https://docs.microsoft.com/en-us/azure/governance/policy/concepts/effects#deployifnotexists-properties
[AzureMonitorScale]: https://docs.microsoft.com/en-us/azure/azure-monitor/deploy-scale
[AzurePolDevOps]: https://techcommunity.microsoft.com/t5/azure-paas-blog/azure-policy-perform-policy-operations-through-azure-devops/ba-p/2045515#:~:text=Login%20to%20your%20Azure%20DevOps%20Organization%20and%20select,Select%20Azure%20Policy%20Deployment%20and%20Click%20on%20Apply
