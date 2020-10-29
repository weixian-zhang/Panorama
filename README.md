### What is Panorama
Panorama is a project about making Azure environment observable, giving Azure users insight to deloyed resources, resource performance, capacity and security.  

#### Artifacts
* Activity Insights
* IaaS Insights
* Firewall Insights
* LogAnalytics Insights
* Inventory Dashboard

#### How to Setup a Workbook
Copy Json content of any Panorama Workbook for example [IaaSInsights](https://github.com/weixian-zhang/Panorama/blob/master/Workbooks/IaaSInsights/IaaSInsights.workbook),  
In Azure Portal, go to **Monitor** and click on Workbook, click **Empty Workbook**  
Follow by clicking on Code icon "</>"  
Under Gallery Template, delete existing Json and paste in IaaSInsights Workbook Json content and hit "Apply"

#### How to Setup a Dashboard  
Save [Inventory Dashboard](https://github.com/weixian-zhang/Panorama/blob/master/InventoryDashboard/Inventory.dashboard) as .json file on your machine.  
Upload .json dashboard.  
<img src="./docs/setup-dashboard.png" width="350" height="200" align="left" />
