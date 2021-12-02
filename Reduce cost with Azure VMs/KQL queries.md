# CPU Utilization (Windows and Linux)

- Data of Last 7 Days
    
      Perf
      | where TimeGenerated > ago(7d)
      | where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
      | where Computer in ((Heartbeat | where OSType == "Linux" or OSType == "Windows" | distinct Computer))
      | summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer

- Data of Last 15 Days
    
      Perf
      | where TimeGenerated > ago(15d)
      | where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
      | where Computer in ((Heartbeat | where OSType == "Linux" or OSType == "Windows" | distinct Computer))
      | summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer
    
- Data of Last 30 Days

      Perf
      | where TimeGenerated > ago(30d)
      | where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"
      | where Computer in ((Heartbeat | where OSType == "Linux" or OSType == "Windows" | distinct Computer))
      | summarize MIN_CPU = min(CounterValue), AVG_CPU = avg(CounterValue), MAX_CPU = max(CounterValue) by Computer

# Memory Utilization (Windows and Linux)
 
- Data of Last 7 Days

      Perf 
      | where ObjectName == "Memory"
      | where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use"
      | where TimeGenerated > ago(7d)
      | summarize MIN_MEMORY = min(CounterValue), AVG_MEMOERY= avg(CounterValue), MAX_MEMORY = max(CounterValue) by Computer

- Data of Last 15 Days
    
      Perf 
      | where ObjectName == "Memory"
      | where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use"
      | where TimeGenerated > ago(15d)
      | summarize MIN_MEMORY = min(CounterValue), AVG_MEMOERY= avg(CounterValue), MAX_MEMORY = max(CounterValue) by Computer
    

- Data of Last 30 Days

      Perf 
      | where ObjectName == "Memory"
      | where CounterName == "% Used Memory" or CounterName == "% Committed Bytes In Use"
      | where TimeGenerated > ago(30d)
      | summarize MIN_MEMORY = min(CounterValue), AVG_MEMOERY= avg(CounterValue), MAX_MEMORY = max(CounterValue) by Computer
