# Policy Setting - MFA should be enabled for accounts with Write Access
![banner]

This policy setting is aimed at reducing attack vectors by ensuring all users who can make changes in the subscription have MFA enabled on their account. If a user has the ability to write to a subscription, resource or resource group they can disrupt or destroy your environments.   

**MFA should be enabled for accounts with write permissions on your subscription**

Multi-Factor Authentication (MFA) should be enabled for all subscription accounts with write privileges to prevent a breach of accounts or resources.

**Information Security Manual**

This policy setting links to [16.7.34 System Architecture and Security Controls CID 6953][CID6953].

Where an agency has implemented MFA they SHOULD:

* Require MFA for administrative or other high privileged users; and
* Implement a secure, multi-factor process to allow users to reset their normal usage user credentials.

## Explanation and instructions

Questions were asked about this specific policy, and if it would be better aligned to a role rather than a permission.  The answer is no due to the fact that there are multiple roles that this could pertain to, along with custom created roles which you would have to define within a policy to ensure all accounts with the ability to influence settings had MFA enabled.

To that end, this policy is driven by the basic Write function instead of the roles, as it captures any role regardless of builtin or custom, that can influence the configuration of your Azure resources.

## Reference Links
* [New Zealand ISM][NZISM]
* [New Zealand Strategy for a Digital Public Service][NZGovDigital]
* [Azure Blueprints Documentation][AzureBP]
* [Azure Blueprint Samples][AzureBPSamples]

<!-- Local -->
[Banner]: images/banner.png
[Blueprint]: images/blueprint.png
[Management]: images/management.png

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
