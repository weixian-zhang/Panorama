<p>
  Panorama is a project about making Azure environment observable, giving Azure users insights to deloyed resources, resource performance, capacity and security
</p>

### Content
* [Workbooks & Dasboard](#workbooks-and-dasboard)
* [Setup Workbook](#setup-a-workbook)
* [Setup Dashboard](#setup-a-Dashboard)
* [Setup Log Collection](#setup-log-collection)

### Workbooks and Dasboard
* Activity Insights
* IaaS Insights
* Firewall Insights
* LogAnalytics Insights
* Inventory Dashboard<br /><br />

### Setup a Workbook
Copy Json content of any Panorama Workbook for example [IaaSInsights](https://github.com/weixian-zhang/Panorama/blob/master/Workbooks/IaaSInsights/IaaSInsights.workbook),  
In Azure Portal, go to **Monitor** and click on Workbook, click **Empty Workbook**  
Follow by clicking on Code icon "</>"  
Under Gallery Template, delete existing Json and paste in IaaSInsights Workbook Json content and hit "Apply"
<img src="./docs/setup-workbook-1.png" width="450" height="250" align="left" />  
<img src="./docs/setup-workbook-2.png" width="450" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />


### Setup a Dashboard  
Save [Inventory Dashboard](https://github.com/weixian-zhang/Panorama/blob/master/InventoryDashboard/Inventory.dashboard) as .json file on your machine.  
Upload .json dashboard.  
<img src="./docs/setup-dashboard.png" width="350" height="200" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

### Setup Log Collection
1. Connect all VMs to Log Analytics Workspace through
   * Azure Portal  
   <img src="./docs/Setuplog-ConnectVMToLaw.png" width="500" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
   * Or through [Powershell](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/vminsights-enable-powershell)<br />
   
2. Add Performance Counters configuration for Log Analytics agent to collect from VMs
