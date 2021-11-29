# Monitoring virtual machine performance with Azure Monitor Application Insights

**InsightsMetrics Queries**

For 7 days:

          InsightsMetrics
          | where TimeGenerated > ago(7d)
          | where Namespace == "Processor"
          | summarize MIN_CPU = min(Val), AVG_CPU = avg(Val), MAX_CPU = max(Val) by Computer
          | join (Heartbeat | distinct Computer,OSType) on Computer
          | project Computer,OSType,MIN_CPU,AVG_CPU,MAX_CPU

<img src="Images/InsightsMetrics CPU 7days.png">

     
For 15 days:

          InsightsMetrics
          | where TimeGenerated > ago(15d)
          | where Namespace == "Processor"
          | summarize MIN_CPU = min(Val), AVG_CPU = avg(Val), MAX_CPU = max(Val) by Computer
          | join (Heartbeat | distinct Computer,OSType) on Computer
          | project Computer,OSType,MIN_CPU,AVG_CPU,MAX_CPU
          
<img src="Images/InsightsMetrics CPU 15days.png">

For 30 days:

          InsightsMetrics
          | where TimeGenerated > ago(30d)
          | where Namespace == "Processor"
          | summarize MIN_CPU = min(Val), AVG_CPU = avg(Val), MAX_CPU = max(Val) by Computer
          | join (Heartbeat | distinct Computer,OSType) on Computer
          | project Computer,OSType,MIN_CPU,AVG_CPU,MAX_CPU
          
<img src="Images/InsightsMetrics CPU 30days.png">

          InsightsMetrics
          | where TimeGenerated > ago(15d)
          | where Namespace == "LogicalDisk" and Name == "FreeSpacePercentage"
          | extend MountID = substring(Tags,22,1)
          | join
          (
              InsightsMetrics
              | where TimeGenerated > ago(15d)
              | where Namespace == "LogicalDisk" and Name == "FreeSpaceMB"
              | extend FreeSpace = (Val/1024)
          ) on Computer
          | join (Heartbeat) on Computer
          | project Computer,OSType,MountID,FreeSpace,Val
