# Reduce Cost with Azure Virtual Machine

VM insights monitors the performance and health of your virtual machines, including their running processes and 
dependencies on other resources. This could be helpful in determining the ways to reduce the cost of Virtual Machine

The cost of the virtual machine depends on various conditions:
- The size of virtual machine
- The region where the VM is deployed
- The operating system of the VM

We will consider some situations for which we can reduce the cost associate to Azure Virtual Machines. For that you should have
Vitual Machines deployed in your subscription.

## Step 1: Create the dependent resources

**Create Log Analytics Workspace**
- Click on **+ Create a resource** in the azure portal and search for **Log Analytics workspace** 
- Select the **+ Create**
- Provide the basic information:

| Setting | Value |
| -- | -- |
| **Subscription** | Select your active subscription |
| **Resource group** | Select the existing resource group or create new |
| **Name** | Sample-LogAnalytics-*selected_region* |
| **Region** | Based on requirement |

- Give the **Tags** to the resource as per requirement.
- Click on the **Review and Create** button. After validation passed **Create** the resource
- Wait for the deployment to complete

## Step 2: Connect the Virtual Machines to Log Analytics Workspace

- Navigate to the previously created **Log Analytics Workspace**
- Under **Workspace Data Sources** section select **Virtual Machines**
- Search for the Virtual Machine in the Search tab, Open the Virtual Machine and then click on **Connect**
- Now, under **Settings** section, click on **Agents configuration**
- Go to **Windows performance counter** tab and click on **Add recommended counters**. Perform the same action on **Linux performance counter**
- Click on **Apply**

## Step 3: Perform some Log Queries

