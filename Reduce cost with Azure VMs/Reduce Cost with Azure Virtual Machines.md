  
  
  Perf
  | where TimeGenerated > ago(7d)
  | where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
  | summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
  | where MAX_CPU < 25

# Reduce Cost with Azure Virtual Machine

VM insights monitors the performance and health of the virtual machines, including their running processes and dependencies on other resources. This could be helpful in determining the ways to reduce the cost of Virtual Machines.

The cost of the virtual machine depends on various conditions:
- The size of virtual machine
- The region where the VM is deployed
- The operating system of the VM

We will consider some situations for which we can reduce the cost associate to Azure Virtual Machines. For that you should have Vitual Machines deployed in your subscription.

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
- Under **Workspace Data Sources** section, select **Virtual Machines**
- Search for the Virtual Machine in the Search tab, Open the Virtual Machine and then click on **Connect**
- Now, under **Settings** section, click on **Agents configuration**
- Go to **Windows performance counter** tab and click on **Add recommended counters**. Perform the same action on **Linux performance counter**
- Click on **Apply**

## Step 3: Perform some Log Queries

- Under **General** section, select **Logs**. Here you can type some Log Queries on which we can decide what action should be performed.
- Some scenarios we can consider such as *Maximum CPU utilization is less than 25, Maximum Memory is less than 25, Free Disk Space is 80% of Total Disk Space*

- Log data for last **7 Days**
- Where Maximum CPU utilization is less than 25

  Perf
  | where TimeGenerated > ago(7d)
  | where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
  | summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
  | where MAX_CPU < 25

- Where Maximum Memory is less than 25

`Perf
| where TimeGenerated > ago(7d)
| where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use" 
| summarize AVG_MEM = avg(CounterValue), MIN_MEM = min(CounterValue), MAX_MEM = max(CounterValue) by Computer
| where MAX_MEM < 25`

- Combination of Maximum CPU utilization and Maximum Memory

`Perf
| where TimeGenerated > ago(7d)
| where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
| summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
| where MAX_CPU < 40
| join
(
    Perf
    | where TimeGenerated > ago(7d)
    | where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use" 
    | summarize AVG_MEM = avg(CounterValue), MIN_MEM = min(CounterValue), MAX_MEM = max(CounterValue) by Computer
    | where MAX_MEM < 40
) on Computer`


- Log data for last **15 Days**

  - Maximum CPU utilization is less than 25
  
`Perf
| where TimeGenerated > ago(15d)
| where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
| summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
| where MAX_CPU < 25`

- Where Maximum Memory is less than 25

`Perf
| where TimeGenerated > ago(15d)
| where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use" 
| summarize AVG_MEM = avg(CounterValue), MIN_MEM = min(CounterValue), MAX_MEM = max(CounterValue) by Computer
| where MAX_MEM < 25`

- Combination of Maximum CPU utilization and Maximum Memory

`Perf
| where TimeGenerated > ago(15d)
| where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
| summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
| where MAX_CPU < 40
| join
(
    Perf
    | where TimeGenerated > ago(15d)
    | where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use" 
    | summarize AVG_MEM = avg(CounterValue), MIN_MEM = min(CounterValue), MAX_MEM = max(CounterValue) by Computer
    | where MAX_MEM < 40
) on Computer`


- Log data for last **30 Days**
  
  - Maximum CPU utilization is less than 25

`Perf
| where TimeGenerated > ago(30d)
| where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
| summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
| where MAX_CPU < 25`

- Where Maximum Memory is less than 25

`Perf
| where TimeGenerated > ago(30d)
| where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use" 
| summarize AVG_MEM = avg(CounterValue), MIN_MEM = min(CounterValue), MAX_MEM = max(CounterValue) by Computer
| where MAX_MEM < 25`

- Combination of Maximum CPU utilization and Maximum Memory

`Perf
| where TimeGenerated > ago(30d)
| where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
| summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
| where MAX_CPU < 40
| join
(
    Perf
    | where TimeGenerated > ago(30d)
    | where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use" 
    | summarize AVG_MEM = avg(CounterValue), MIN_MEM = min(CounterValue), MAX_MEM = max(CounterValue) by Computer
    | where MAX_MEM < 40
) on Computer`

- Free Disk Space is 80% of Total Disk Space

## Step 4: Resize the Virtual Machine

- Navigate to the Virtual Machine that we found from the log queries
- First **Stop** the Virtual Machine
- Under **Settings** section, go to **Size**
- Select the size of the Virtual Machine, which has less number of vCPUs, RAM so the cost should be less compared to others.
> Note: If the virtual machine is in running state, changing the size will cause it to be restarted.
- Click on **Resize**, once you selected the desired size for virtual machine
