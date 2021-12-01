# Monitoring virtual machine performance with Azure Monitor Application Insights

**InsightsMetrics Queries**

CPU utilization of virtual machine for last 7 days:

          InsightsMetrics
          | where TimeGenerated > ago(7d)
          | where Namespace == "Processor"
          | summarize MIN_CPU = min(Val), AVG_CPU = avg(Val), MAX_CPU = max(Val) by Computer
          | join (Heartbeat | distinct Computer,OSType) on Computer
          | project Computer,OSType,MIN_CPU,AVG_CPU,MAX_CPU

<img src="Images/InsightsMetrics CPU 7days.png">

     
CPU utilization of virtual machine for last 15 days:

          InsightsMetrics
          | where TimeGenerated > ago(15d)
          | where Namespace == "Processor"
          | summarize MIN_CPU = min(Val), AVG_CPU = avg(Val), MAX_CPU = max(Val) by Computer
          | join (Heartbeat | distinct Computer,OSType) on Computer
          | project Computer,OSType,MIN_CPU,AVG_CPU,MAX_CPU
          
<img src="Images/InsightsMetrics CPU 15days.png">

CPU utilization of virtual machine for last 30 days:

          InsightsMetrics
          | where TimeGenerated > ago(30d)
          | where Namespace == "Processor"
          | summarize MIN_CPU = min(Val), AVG_CPU = avg(Val), MAX_CPU = max(Val) by Computer
          | join (Heartbeat | distinct Computer,OSType) on Computer
          | project Computer,OSType,MIN_CPU,AVG_CPU,MAX_CPU
          
<img src="Images/InsightsMetrics CPU 30days.png">


Percentage free space of disk from last 15 days

          InsightsMetrics
          | where TimeGenerated > ago(15d)
          | where Namespace == "LogicalDisk" and Name == "FreeSpacePercentage"
          | extend MountID = substring(Tags,22,1)
          | extend FreePercentage = Val
          | join
          (
              InsightsMetrics
              | where TimeGenerated > ago(15d)
              | where Namespace == "LogicalDisk" and Name == "FreeSpaceMB"
              | extend FreeSpace = (Val/1024)
          ) on Computer
          | join (Heartbeat) on Computer
          | extend Total = (FreeSpace*100)/FreePercentage
          | project Computer,OSType,MountID,FreeSpace,Total,FreePercentage

