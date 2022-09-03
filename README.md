# Cascade-Tags

## Introduction 

Managing tags is a critical aspect of a well-rounded Azure governance strategy.  Propper tagging supports a number of functions including general resource management,  automation, operations, cost management & optimization, security, and regulatory compliance.  In order to support these functions, proper tagging should be enforced throughout the entire lifecycle of a resource.  This includes defining an enterprise tagging strategy and then using Azure Policy to enforce those requirements.  Unfortunately, there are several scenarios that Azure Policy does not address in a graceful or comprehesive manner.  This **Cascade-Tag** Powershell solution is intended to help close those gaps with the use of Azure Automation to ensure tags from Subscriptions and Resource Groups are updated on child resources.

[Available Azure Tag Compliance Policies](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/tag-policies)

A common strategy for tagging resources involves inheriting certain Tags and Values from a parent resource with Azure Policy providing out-of-the-box definitions to support this.  While this seems like a complete solution to set an establish an initial baseline for tags, there are a few short comings with this approach.

1. If you implemented your tagging strategy after you had already deployed resources, Azure Policy will not take effect.  Azure Policy executes during the create and update operations of a resource, and you would need to execute a Remediation Task to populate tags on those existing resources.

2. The second, and more common, situation is when new tags are created or changed on the parent and don't immediately cascade to the child resources.  To better illustrate, let's assume you have a Department tag specified at the Resource Group level for an application consisting of a number of child resources.  Further, this application is being transferred to a new department that will be responsible for the hosting costs going forward.  If you update the tag value on the Resource Group, it will not cascade to the child resources, because Azure Policy will only fire when a child resource is created or updated.  In this example, the change occured on the resource group and not the individual resources and you have mismatched tags between the two.  The only way to resolve this discrepancy is to execute a remediation task or cause the update action of each resource within the resource group.

By deploying

## Deployment Instructions 
 + Imports FHIR Bundles (compressed and non-compressed) and NDJSON files into a FHIR service 
 + High Speed Parallel Event Grid that triggers from storage accounts or other event grid resources
 + Complete Auditing, Error logging and Retry for throttled transactions
 + High Speed Parallel Orchestrated Patient-centric Export Capability 
