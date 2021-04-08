# Policy Setting - Users included\excluded in VM Administrators Group
![banner]

<br/>

There are two policy settings defined in the initiative relating to IaaS Windows Virtual machines, and are primarily focussed on heritage infrastructure that utilizes management techniques that have been superseded in PaaS or SaaS.

**Audit Windows machines missing any of specified members in the Administrators group**

Requires that prerequisites are deployed to the policy assignment scope. For details, visit https://aka.ms/gcpol. Machines are non-compliant if the local Administrators group does not contain one or more members that are listed in the policy parameter.

**Audit Windows machines that have extra accounts in the Administrators group**

Requires that prerequisites are deployed to the policy assignment scope. For details, visit https://aka.ms/gcpol. Machines are non-compliant if the local Administrators group contains members that are not listed in the policy parameter.

**Information Security Manual**

These policy settings link to [16.1.32 System User Identification CID. 1829][CID1829].

## Explanation
The first of these policies are designed to ensure that break glass accounts, or IaaS management accounts are present in all Windows virtual machines.  In a heritage environment or primarily IaaS focused infrastructure, it is not uncommon to have one, or a series of accounts that have access to these virtual machines.  However, during provisioning or maintenance these accounts can be omitted or removed, and cause a potential blind spot in the management and security infrastructure.  Therefore it is recommended to ensure you maintain a list of these accounts and ensure at least one has access to the virtual machine.

The second policy monitors the converse, and reports when any account outside the defined list of accounts is added to the local administrators group.  This can occur for several reasons from malicious activity to a requirement for elevated access to resolve an issue, or even hangover from previous activity such as application deployment.  An example might be an administrator has worked late into the night to fix an issue, and has not removed temporary elevated permissions once the fix is complete.  This presents a security risk in the event of credential compromise, so the audit function can alert the administrator to take corrective action.

As both of these policies be utilized in conjunction with [Azure ARC][AzureArc] this can also monitor the virtual infrastructure in other non-Azure environments to report across the entire enterprise.  

## Management

To ensure that this reports your compliance correctly it would be recommended to add all of the accounts expected to be seen in the Local Administrators group on any of your IaaS virtual machines into these two lists.  This ensures that as long as one of those accounts, or if an account outside this list appears, it will be identified.

Alternatively, if you are managing this in another way, you can simply enter a double open\closed square bracket [] and override the policy audit with an explanation to ensure you are compliant.  This also applies to agencies that have disposed of all infrastructure requiring this management technique.  Nice work if thats the case :)


## Reference Links
* [New Zealand ISM][NZISM]
* [New Zealand Strategy for a Digital Public Service][NZGovDigital]
* [Azure Blueprints Documentation][AzureBP]
* [Azure Blueprint Samples][AzureBPSamples]
* [Azure Arc][AzureArc]

<!-- Local -->
[Banner]: images/banner.png

<!-- External -->
[NZISM]: https://www.nzism.gcsb.govt.nz/ism-document
[AzureBP]: https://docs.microsoft.com/en-us/azure/governance/blueprints/overview
[AzureBPSamples]: https://docs.microsoft.com/en-us/azure/governance/blueprints/samples/
[NZGovDigital]: https://www.digital.govt.nz/digital-government/strategy/strategy-summary/strategy-for-a-digital-public-service/
[CID1829]: https://www.nzism.gcsb.govt.nz/ism-document#1829
[AzureArc]: https://docs.microsoft.com/en-us/azure/azure-arc/