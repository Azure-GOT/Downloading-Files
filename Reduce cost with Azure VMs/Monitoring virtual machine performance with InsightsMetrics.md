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


