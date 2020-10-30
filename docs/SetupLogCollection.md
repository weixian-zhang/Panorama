### Setup Log Collection
1. Connect all VMs to Log Analytics Workspace through
   * Azure Portal  
     <img src="Setuplog-ConnectVMToLaw.png" width="500" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
   * Or through [Powershell](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/vminsights-enable-powershell)<br /><br />
   
2. Add Linux and Windows Performance Counters configuration for Log Analytics agent to collect from VMs
    <img src="Setuplog-AddPerfCounters.png" width="550" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

3. Enable Azure Monitor for VM  
   <img src="Setuplog-EnableMonitorForVM.png" width="550" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

4. Enable Change Tracking  
   <img src="Setuplog-EnableChangeTracking.png" width="450" height="300" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
