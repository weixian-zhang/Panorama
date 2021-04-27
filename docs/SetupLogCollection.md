### Setup Log Collection  

1. [Connect VMs To Log Analytics](#connect-vms-to-log-analytics)
2. [Setup Performance Counters](#setup-performance-counters)
3. [Enable Azure Monitor for VM](#enable-azure-monitor for VM)
4. [Enable Update Management](#enable-update-management)
5. [Enable Inventory & Change Tracking](#enable-inventory--change-tracking)
6. [Activity Log to Log Analytics Workspace](#activity-log-to-log-analytics-workspace)
7. [Enable NSG Flow logs & Traffic Analytics](#nsg-flow-logs--traffic-analytics)
8. [Add Network Performance Monitoring solution](#network-performance-monitor-solution)

####  Connect VMs to Log Analytics
* Azure Portal  
  <img src="Setuplog-ConnectVMToLaw.png" width="500" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
* Or through [Powershell](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/vminsights-enable-powershell)<br /><br />
   
#### Setup Performance Counters    
Add Linux and Windows Performance Counters configuration for Log Analytics agent to collect from VMs  
<img src="Setuplog-AddPerfCounters.png" width="550" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

#### Enable Azure Monitor for VM 
<img src="Setuplog-EnableMonitorForVM.png" width="550" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

#### Enable Update Management
[See docs](https://docs.microsoft.com/en-us/azure/automation/update-management/enable-from-vm)
   
#### Enable Inventory & Change Tracking
[See docs](https://docs.microsoft.com/en-us/azure/automation/change-tracking/enable-from-vm)
<img src="Setuplog-EnableChangeTracking.png" width="450" height="300" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />  
   
#### Activity Log to Log Analytics Workspace  
[Activity Log Categories](https://docs.microsoft.com/en-us/azure/azure-monitor/platform/activity-log-schema#categories)

<img src="Setuplog-ActivityLog-DiagnosticSettings.png" width="500" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
<img src="Setuplog-ActivityLog-DiagnosticSettings-2.png" width="550" height="350" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

#### NSG Flow logs & Traffic Analytics
Go to Network Watcher -> NSG Flow logs and watch out for NSG with Status "Disabled".  
Select NSG with Disabled status and select
   * Flow logs = "On"
   * Flow Logs version = 2
   * select a storage account to keep the raw logs
   * Go to Traffic Analytics status switch to "On" to enable Traffic Analytics
   * select Log Analytics to store aggregated logs of Traffic Analytics

#### Network Performance Monitor solution  
Follow [this doc](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/network-performance-monitor) to setup NPM
