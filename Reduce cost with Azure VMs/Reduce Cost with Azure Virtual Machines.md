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
- Some scenarios we can consider such as *Maximum CPU utilization is less than 25, Maximum Memory utilization is less than 25, Free Disk Space is 80% of Total Disk Space*

- Log data for last **7 Days** of Virual Machine Performance. 
- Here the **Perf** is the performance of hardware components operating systems and applications. We are providing the minimum, average, maximum CPU utilization and minimum, average, maximum Memory utilization from last 7 days. Based on that we are filtering the result where the maximum CPU utilization is less than 25 and maximum Memory utilization is less than 25. 
- In the Memory part, *% Committed Bytes In Use* is for Windows and *% Used Memory* is for Linux

- Where Maximum CPU utilization is less than 25

        Perf
        | where TimeGenerated > ago(7d)
        | where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
        | summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
        | where MAX_CPU < 25

- Where Maximum Memory utilization is less than 25

        Perf
        | where TimeGenerated > ago(7d)
        | where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use" 
        | summarize AVG_MEM = avg(CounterValue), MIN_MEM = min(CounterValue), MAX_MEM = max(CounterValue) by Computer
        | where MAX_MEM < 25

- Consolidated chart of Maximum CPU utilization and Maximum Memory utilization

        Perf
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
        ) on Computer

<img src="Images/Log-Query-7days.png">

- Log data for last **15 Days** of Virual Machine Performance.
- Here the **Perf** is the performance of hardware components operating systems and applications. We are providing the minimum, average, maximum CPU utilization and minimum, average, maximum Memory utilization from last 15 days. Based on that we are filtering the result where the maximum CPU utilization is less than 25 and maximum Memory utilization is less than 25
- In the Memory part, *% Committed Bytes In Use* is for Windows and *% Used Memory* is for Linux

  - Maximum CPU utilization is less than 25
  
        Perf
        | where TimeGenerated > ago(15d)
        | where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
        | summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
        | where MAX_CPU < 25

- Where Maximum Memory utilization is less than 25

        Perf
        | where TimeGenerated > ago(15d)
        | where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use" 
        | summarize AVG_MEM = avg(CounterValue), MIN_MEM = min(CounterValue), MAX_MEM = max(CounterValue) by Computer
        | where MAX_MEM < 25

- Consolidated chart of Maximum CPU utilization and Maximum Memory utilization

        Perf
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
        ) on Computer

<img src="Images/Log-Query-15days.png">

- Log data for last **30 Days** of Virual Machine Performance.
- Here the **Perf** is the performance of hardware components operating systems and applications. We are providing the minimum, average, maximum CPU utilization and minimum, average, maximum Memory utilization from last 30 days. Based on that we are filtering the result where the maximum CPU utilization is less than 25 and maximum Memory utilization is less than 25
- In the Memory part, *% Committed Bytes In Use* is for Windows and *% Used Memory* is for Linux

  - Maximum CPU utilization is less than 25

        Perf
        | where TimeGenerated > ago(30d)
        | where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
        | summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
        | where MAX_CPU < 25

- Where Maximum Memory utilization is less than 25

        Perf
        | where TimeGenerated > ago(30d)
        | where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use" 
        | summarize AVG_MEM = avg(CounterValue), MIN_MEM = min(CounterValue), MAX_MEM = max(CounterValue) by Computer
        | where MAX_MEM < 25

- Consolidated chart of Maximum CPU utilization and Maximum Memory utilization

        Perf
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
        ) on Computer

<img src="Images/Log-Query-30days.png">

- Free Disk Space is 80% of Total Disk Space

## Step 4: Resize the Virtual Machine

- Navigate to the Virtual Machine that we found from the log queries
- First **Stop** the Virtual Machine
- Under **Settings** section, go to **Size**
- Select the size of the Virtual Machine, which has less number of vCPUs, RAM so the cost should be less compared to others.
> Note: If the virtual machine is in running state, changing the size will cause it to be restarted.
- Click on **Resize**, once you selected the desired size for virtual machine

## Step 5: Reduce the size of OS Disk

## Step 6: Create the Metrics chart from Azure Monitor

- To monitor the virtual machines individualy we can use Metrics chart
- Navigate to the Azure monitor, click on **Metrics**
- First it will ask for Select a scope, you can select only one resource here
- After selecting the resource, select the required Metric and aggregation
- You can pin this metric chart to dashboard by clicking **Pin to dashboard** from the top menu

## Step 7: Adding the data to Dashboard

- To visualize the all collected data in one place, we can create one dashboard for that.
- On the left corner side of the Azure portal, click on the Menu option and select **Dashboard**
- Click on the **+ New dashboard** from the top menu and select Blank dashboard.
- Give the new name of dashboard and click on Done customizing.
- When you perform any operation in the portal there is an option **Pin to dashboard**. Simply click on that
- Select the existing Dashboard available or create the new one from here.
- After that click on **Pin**, the data then will be available on the dashboard.

## Step 8: Add the alerts 

The users should get notification when some conditions met like when there is a resource which is not properly utilized for last some days, the cost can be reduced for such resouces.

- When writing the log queries there is an option for the **+ New alert rule** in the top menu. This will be based on that specific query.
- Click on that, the condition should be already there define the logic in that condition
- Now click on the **Add action group**, in that we can add the email address or SMS for the required user which will be notified 
