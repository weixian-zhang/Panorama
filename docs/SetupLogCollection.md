### Setup Log Collection
1. Connect all VMs to Log Analytics Workspace through
   * Azure Portal  
     <img src="Setuplog-ConnectVMToLaw.png" width="500" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
   * Or through [Powershell](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/vminsights-enable-powershell)<br /><br />
   
2. Add Linux and Windows Performance Counters configuration for Log Analytics agent to collect from VMs
    <img src="Setuplog-AddPerfCounters.png" width="550" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

3. Enable Azure Monitor for VM  
   <img src="Setuplog-EnableMonitorForVM.png" width="550" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

4. Enable [Service Map solution](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/service-map#enable-service-map)  
   <img src="Setuplog-ServiceMapSolution-1.png" width="400" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
   <img src="Setuplog-ServiceMapSolution-2.png" width="400" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
   
5. Enable Change Tracking  
   <img src="Setuplog-EnableChangeTracking.png" width="450" height="300" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
   
6. Activity Log to Log Analytics Workspace  
   <img src="Setuplog-ActivityLog-DiagnosticSettings.png" width="500" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
   <img src="Setuplog-ActivityLog-DiagnosticSettings-2.png" width="550" height="350" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
