# Policy Setting - Web Application Firewall (WAF) should be enabled for Application Gateway

![banner]

<br/>

This policy is to ensure that if you deploy an Application Gateway, you should also deploy the WAF component ahead of it, to increase the security capability of the public endpoint.

**Web Application Firewall (WAF) should be enabled for Application Gateway**

Deploy Azure Web Application Firewall (WAF) in front of public facing web applications for additional inspection of incoming traffic. Web Application Firewall (WAF) provides centralized protection of your web applications from common exploits and vulnerabilities such as SQL injections, Cross-Site Scripting, local and remote file executions. You can also restrict access to your web applications by countries, IP address ranges, and other http(s) parameters via custom rules.

**Information Security Manual**

This policy setting links to [18.4.10.Malicious code counter-measures CID3851][CID3851]

Agencies MUST:

Develop and maintain a set of policies and procedures covering how to:
* minimise the likelihood of malicious code being introduced into a system;
* prevent all unauthorised code from executing on an agency network; 
* detect any malicious code installed on a system;
* make their system users aware of the agency’s policies and procedures; and
* ensure that all instances of detected malicious code outbreaks are handled according to established procedures.

## Explanation
Any public facing endpoint must have different methods of controlling the many vectors of attack that bad actors on the internet utilise to gain access.  The WAF is one of those controls, and should always be used to reduce the ability of bad actors from gaining a foothold in your enterprise.

A question was asked on how to stay compliant against the NZISM Policy initiative when resources such as the WAF are not needed, but an Application Gateway actually is.  Some instances for this might be:
* the environment does not contain or have access to classified information (sandpit, Dev\Test or disconnected POC environments)
* the Application gateway is only utilised for internal traffic only


These are valid concerns, and there are two main paths to establish how you determine how to maintain compliancy without deploying unnecessary resources.  

The first would be to refer to the Azure Reference Architecture site and review the [Firewall and Application Gateway for Virtual Networks][AzureWAFRefArch].  This guide goes in depth on Azure Firewall, App Gateway and WAF, and decision trees on when each is recommended to be used.

The second is your own risk and compliance assessment capability - this is your risk as an agency, so the final say rests in your hands!  Review the information passing through the gateway and its classification, what other controls you have in place and consult with the business owners.

If you determine that it is not required, you can create an exemption in the Azure Policy console for that resource, and document why it is not required.

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
[CID3851]: https://www.nzism.gcsb.govt.nz/ism-document#3851
[AzureWAFRefArch]: https://docs.microsoft.com/en-us/azure/architecture/example-scenario/gateway/firewall-application-gateway