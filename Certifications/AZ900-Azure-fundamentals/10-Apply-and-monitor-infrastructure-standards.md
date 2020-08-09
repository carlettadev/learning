[< Previous](9-Security-responsibility-and-trust-in-Azure.md) - [Next >]()

# 10 - Apply and monitor infrastructure standards with Azure Policy

Learn about governance and management in Azure services.

## Intro [^1]

Good IT governance involves planning your initiatives and setting priorities on a strategic level to help manage and prevent issues.

You need good governance when:

- You have multiple engineering teams working in Azure
- You have multiple subscriptions in your tenant
- You have regulatory requirements that must be enforced
- You want to ensure standards are followed for all IT allocated resources

You could enforce standards by not allowing teams to directly create Azure resources - and instead have the IT team define and deploy all cloud-based assets. This approach is often the solution in on-premises situations, but this requirement reduces the team agility and ability to innovate. Instead, Azure provides several tools you can use to enforce and validate your standards, while still allowing your engineering teams to create and own their own resources in the cloud.

## Define IT compliance with Azure Policy [^2]

Planning out a consistent cloud infrastructure starts with setting up policy. Your policies will enforce your rules for created resources, so your infrastructure stays compliant with your corporate standards, cost requirements, and any service-level agreements (SLAs) you have with your customers.

__Azure Policy__ is an Azure service you use to create, assign and, manage policies. These policies enforce different rules and effects over your resources so that those resources stay compliant with your corporate standards and service level agreements. Azure Policy meets this need by evaluating your resources for noncompliance with assigned policies. For example, you might have a policy that allows virtual machines of only a certain size in your environment. After this policy is implemented, new and existing resources are evaluated for compliance. With the right type of policy, existing resources can be brought into compliance.

Imagine we allow anyone in our organization to create virtual machines (VMs). We want to control costs, so the administrator of our Azure tenant defines a policy that prohibits the creation of any VM with more than 4 CPUs. Once the policy is implemented, Azure Policy will stop anyone from creating a new VM outside the list of allowed stock keeping units (SKUs). Also, if you try to _update_ an existing VM, it will be checked against policy. Finally, Azure Policy will audit all the existing VMs in our organization to ensure our policy is enforced. It can audit non-compliant resources, alter the resource properties, or stop the resource from being created. You can even integrate Azure Policy with Azure DevOps, by applying any continuous integration and delivery pipeline policies that affect the pre-deployment and post-deployment of your applications.

### How are Azure Policy and RBAC different?

At first glance, it might seem like Azure Policy is a way to restrict access to specific resource types similar to role-based access control (RBAC). However, they solve different problems. RBAC focuses on user actions at different scopes. You might be added to the contributor role for a resource group, allowing you to make changes to anything in that resource group. Azure Policy focuses on resource properties during deployment and for already-existing resources. Azure Policy controls properties such as the types or locations of resources. Unlike RBAC, Azure Policy is a default-allow-and-explicit-deny system.

### Create a policy

The process of creating and implementing an Azure Policy begins with creating a policy definition. Every policy definition has conditions under which it is enforced. And, it has an accompanying effect that takes place if the conditions are met. To apply a policy, you will:

- Create a policy definition
- Assign a definition to a scope of resources
- View policy evaluation results


### What is a policy definition?

A policy definition expresses what to evaluate and what action to take. For example, you could ensure all public websites are secured with HTTPS, prevent a particular storage type from being created, or force a specific version of SQL Server to be used.

Here are some of the most common policy definitions you can apply.

|       Policy definition      |                                                                                                                      Description                                                                                                                     |
|:----------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Allowed Storage Account SKUs | This policy definition has a set of conditions/rules that determine  whether a storage account that is being deployed is within a set of SKU  sizes. Its effect is to deny all storage accounts that do not adhere to  the set of defined SKU sizes. |
| Allowed Resource Type        | This policy definition has a set of conditions/rules to specify the  resource types that your organization can deploy. Its effect is to deny  all resources that are not part of this defined list.                                                  |
| Allowed Locations            | This policy enables you to restrict the locations that your  organization can specify when deploying resources. Its effect is used to  enforce your geographic compliance requirements.                                                              |
| Allowed Virtual Machine SKUs | This policy enables you to specify a set of VM SKUs that your organization can deploy.                                                                                                                                                               |
| Not allowed resource types   | Prevents a list of resource types from being deployed.                                                                                                                                                                                               |

The policy definition itself is represented as a JSON file - you can use one of the pre-defined definitions in the portal or create your own (either modifying an existing one or starting from scratch). There are hundreds of samples available on GitHub.

Here is an example of a Compute policy that only allows specific virtual machine SKUs:

```JSON
{
  "if": {
    "allOf": [
      {
        "field": "type",
        "equals": "Microsoft.Compute/virtualMachines"
      },
      {
        "not": {
          "field": "Microsoft.Compute/virtualMachines/sku.name",
          "in": "[parameters('listOfAllowedSKUs')]"
        }
      }
    ]
  },
  "then": {
    "effect": "Deny"
  }
}
```

Notice the _[parameters('listofAllowedSKUs')]_ value; this value is a replacement token that will be filled in when the policy definition is applied to a scope. When a parameter is defined, it's given a name and optionally given a value.

## Organize policy with initiatives [^3]

Managing a few policy definitions is easy, but once you have more than a few, you will want to organize them. That's where _initiatives_ come in.

Initiatives work alongside policies in Azure Policy. An initiative definition is a set or group of policy definitions to help track your compliance state for a larger goal. Even if you have a single policy, we recommend using initiatives if you anticipate increasing the number of policies over time.

Like a policy assignment, an _initiative assignment_ is an initiative definition assigned to a specific scope. Initiative assignments reduce the need to make several initiative definitions for each scope. This scope could also range from a management group to a resource group.

### Defining initiatives

Initiative definitions simplify the process of managing and assigning policy definitions by grouping a set of policies into a single item. For example, you could create an initiative named _Enable Monitoring_ in Azure Security Center, with a goal to monitor all the available security recommendations in your Azure Security Center.

Under this initiative, you would have the following policy definitions:

|                    Policy definition                   |                                 Purpose                                |
|:------------------------------------------------------:|:----------------------------------------------------------------------:|
| Monitor unencrypted SQL Database in Security Center    | For monitoring unencrypted SQL databases and servers.                  |
| Monitor OS vulnerabilities in Security Center          | For monitoring servers that do not satisfy the configured baseline.    |
| Monitor missing Endpoint Protection in Security Center | For monitoring servers without an installed endpoint protection agent. |

## Manage access, policies, and compliance across multiple Azure subscriptionsManage access, policies, and compliance across multiple Azure subscriptions [^4]

Access management occurs at the Azure subscription level. This control allows an organization to configure each division of the company in a specific fashion based on their responsibilities and requirements. Planning and keeping rules consistent across subscriptions can be challenging without a little help.

[< Previous](9-Security-responsibility-and-trust-in-Azure.md) - [Next >]()

[^1]: https://docs.microsoft.com/en-us/learn/modules/intro-to-governance/1-introduction
[^2]: https://docs.microsoft.com/en-us/learn/modules/intro-to-governance/2-azure-policy
[^3]: https://docs.microsoft.com/en-us/learn/modules/intro-to-governance/3-initiatives
[^4]: https://docs.microsoft.com/en-us/learn/modules/intro-to-governance/4-management-groups