# Policy Setting - MFA should be enabled for accounts with Write\Read\Owner Access
![banner]

These policies relate to the accounts within your subscriptions that have write access, owner permissions or read access.  These accounts can have the ability to severely compromise your enterprise, so mitigation's should be used to reduce the likelihood of an attack, or reduce the surface area.  These policies include mitigation such as enabling MFA for any account that has read or write access to a subscription, or is an owner of a subscription.  They also include identification of accounts that have been disabled or had access revoked, or an external account that has permission to a subscription.   

**MFA should be enabled for accounts with write permissions on your subscription**

Multi-Factor Authentication (MFA) should be enabled for all subscription accounts with write privileges to prevent a breach of accounts or resources.

**Information Security Manual**

This policy setting links to [16.7.34 System Architecture and Security Controls CID 6953][CID6953].

Where an agency has implemented MFA they SHOULD:

* Require MFA for administrative or other high privileged users; and
* Implement a secure, multi-factor process to allow users to reset their normal usage user credentials.

## Other linked Policies
There are several other policies that are similar in nature to the one at the top of the article.  They are:

* MFA should be enabled on accounts with owner permissions on your subscription
* MFA should be enabled on accounts with read permissions on your subscription
* External accounts with write permissions should be removed from your subscription
* External accounts with owner permissions should be removed from your subscription
* Deprecated accounts should be removed from your subscription
* Deprecated accounts with owner permissions should be removed from your subscription

## Explanation and instructions

Questions were asked about the "write permission" policy, and if it would be better aligned to a role rather than a permission.  The answer is no due to the fact that there are multiple roles that this could pertain to, along with custom created roles which you would have to define within a policy to ensure all accounts with the ability to influence settings had MFA enabled.

To that end, this policy is driven by the basic Write function instead of the roles, as it captures any role regardless of builtin or custom, that can influence the configuration of your Azure resources.

The other area of concern which covers all of the policies listed in this article, was around identifying the specific accounts that each of the policies may identify.  The triggers for non-compliance are different, but the usage of the console and identification of the non-compliant object is the same.

Unfortunately, if you use the Policy console and drill into the non-compliant object, you do not receive any detail on the account that is non-compliant.  This is because it is examining the property of the Object (which is the Subscription) and if you click on the View Resource button it will simply take you to the non-compliant object.  Not helpful really I know.

However you can view the detail through the Security Center.  First, click on the policy that is non-compliant to view the details and note the Parent Control (in this picture below, that is 12.4.4 Patching Vulnerabilities)

![PolicyMFA1]

Then go to the Security Center, and click on Regulatory Compliance, and click on the New Zealand ISM Restricted.  If you dont see this, you need to click the Manage Compliance policies at the top and ensure the NZ ISM Policy Initiative is listed there.

![PolicyMFA2]

Scroll down the list to find your control and expand the specific control which should show the policies that link to that control.

![PolicyMFA3]

Click on the non-compliant control, and then click on the Unhealthy Resource.  A screen listing the accounts that are non-compliant will appear on the right hand side of the screen.

![PolicyMFA4]

This will help you get to a list of accounts quickly, to allow you to remediate which accounts are non-compliant.  The other key takeaway of course should be to identify how those accounts became non-compliant, and try and resolve the source of the issue.  For example, if an external account has write access it should be identified how this was granted, and block that pathway through change in business process or policy enforcement on your Azure subscriptions.

## Reference Links
* [New Zealand ISM][NZISM]
* [New Zealand Strategy for a Digital Public Service][NZGovDigital]
* [Azure Blueprints Documentation][AzureBP]
* [Azure Blueprint Samples][AzureBPSamples]

<!-- Local -->
[Banner]: images/banner.png
[Blueprint]: images/blueprint.png
[Management]: images/management.png
[PolicyMFA1]: images/policymfa1.png
[PolicyMFA2]: images/policymfa2.png
[PolicyMFA3]: images/policymfa3.png
[PolicyMFA4]: images/policymfa4.png

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
[CID6953]: https://www.nzism.gcsb.govt.nz/ism-document#6953
