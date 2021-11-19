# Reduce Cost with Azure Virtual Machine

VM insights monitors the performance and health of your virtual machines, including their running processes and 
dependencies on other resources. This could be helpful in determining the ways to reduce the cost of Virtual Machine

The cost of the virtual machine depends on various conditions:
- The size of virtual machine
- The region where the VM is deployed
- The operating system of the VM

We will consider some situations for which we can reduce the cost associate to Azure Virtual Machines. For that you should have
Vitual Machines deployed in your subscription.

**Step1:** Create the dependent resources

1. Create Log Analytics Workspace
- Click on **+ Create a resource** in the azure portal and search for **Log Analytics workspace** 
- Select the **+ Create**
- Provide the basic information:
| Setting | Value |
| -- | -- |
| **Subscription** | Select your active subscription |
| **Resource group** | Select the existing resource group or create new |
| **Name** | Sample-LogAnalytics-*selected_region* |
| **Region** | Based on requirement |

