
  Panorama is a project about making Azure environment observable, giving Azure users insights to deloyed resources, performance, and security. Certain KQLs are adapted from [Azure Monitor Community](https://github.com/microsoft/AzureMonitorCommunity).  
  The workbooks does not currently contain Location parameter, as workbooks and dashboard are built for the purpose of a local Goverment Commercial Cloud program where all resources are in Southeast Asia region.  

### Content
[What Panorama offers?](#what-panorama-offers)  
[Artifacts - Workbooks & Dasboard](#workbooks-and-dasboard)  
[How to setup a Workbook](#setup-a-workbook)  
[How to setup a Dashboard](#setup-a-dashboard)  
[Collect Logs](https://github.com/weixian-zhang/Panorama/blob/master/docs/SetupLogCollection.md)  
[Guide - Azure Network Monitoring Tools](#network-monitoring-guide)  

### What Panorama Offers  
Panorama contains supplementry monitoring viewpoints in the form of Workbooks and Dashboard in addition to existing community and built-in Azure workbooks.
The workbooks are built on requirements gathered from a local goverment commercial cloud program and some differentiating info these workbooks provide are:
- [x] What NSG rules are being created or updated, who did it and when?
- [x] What Azure Firewall rules are being created or updated categorized by NAT, Network and App rules, who did it and when?
- [x] What are the Threats Azure Firewall has protected me against? IP of the source of threats and when?
- [x] A summary of all writes and deletes happening in my environment, who did it and when
- [x] What are the network traffics within a VNet(Intra-VNet), inter-peered VNets, to and from between any External Public IPs or Azure-owned control-plane Public IPs?
- [x] For each of my VM, how much disk space does each logical drive are left with?
- [x] How much memory available currently out of total VM memory?
- [x] Which VMs have missing Critical and Security Patches and what are the missing patches?

### Workbooks and Dasboard  
Panorama consists of the following artifacts:  
* Workbooks  
   * [Activity Insights](#activity-insights-workbook)
   * [IaaS Insights](#iaas-insights-workbook)
   * [LogAnalytics Insights](#log-analytics-insights-workbook)
   * [Traffic Search](#traffic-search)
   * Key Vault Audit Insights (coming soon...)
* Dashboard
   * [Inventory Dashboard](#inventory-dashboard)  

### Setup a Workbook
1. Copy Json content of any Panorama Workbook for example [IaaSInsights](https://github.com/weixian-zhang/Panorama/blob/master/Workbooks/IaaSInsights/IaaSInsights.workbook),  
2. In Azure Portal, go to **Monitor** and click on Workbook, select **Empty Workbook**  
3. Follow by clicking Code icon "</>"  
4. Under **Gallery Template**, delete existing Json and paste in IaaSInsights Workbook Json content and hit "Apply"
   <img src="./docs/setup-workbook-1.png" width="450" height="250" align="left" />  
   <img src="./docs/setup-workbook-2.png" width="450" height="250" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

### Setup a Dashboard  
1. Save [Inventory Dashboard](https://github.com/weixian-zhang/Panorama/blob/master/InventoryDashboard/Inventory.dashboard) as .json file on your machine.  
2. Upload .json dashboard.  
   <img src="./docs/setup-dashboard.png" width="350" height="200" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

### Activity Insights Workbook    
* all general resource writes and deletes of your Azure environment
* Network Security Group changes, who made the change, what is the exact rule and the value changed. E.g: Access change from Deny to Allow, Destination Address to */Any.
* Azure Firewall rule changes, who made the change, a breakdown on exactly which NAT, Network and/or Application Rule is changed and the vault of change

### IaaS Insights Workbook  
This workbook contains 5 tabs:  
* VM Availability: A simple graph view of Azure Health metrics. Green means VM is available, Orange can means stopped or not available for whatever reasons.
* CPU & Memory: This gives you the details of each VM what is the current CPU consupmtion in % and the number of cores. For memory, it shows the Available Memory out of Total Memory of the VM spec.
* Disk Capacity: Breaks down all drives attached to each VM and shows the free space in each drive. ([D drive](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/change-drive-letter) is a temp drive). Any disk lesser 15GB of free space will be marked Red.
* Patch Status: This tab gives you a <em>Grid Summary and Detail</em> view where you can select a VM in the Summary Table while the Details Table below shows you which patches are missing.  
* Change Tracking: Showcase 5 areas of changes: File, Windows Services, Linux Daemons, Software and Registry

### Firewall Insights Workbook  
Use official [Azure Monitor Workbook For Firewall](https://github.com/Azure/Azure-Network-Security/tree/master/Azure%20Firewall/Workbook%20-%20Azure%20Firewall%20Monitor%20Workbook) instead.  
*Firewall Insights is obsolete

### Log Analytics Insights Workbook  
It operates 1 workspace at a time, contains a view of ingested logs in GB grouped by Monitoring Solution, and Kubernetes specific logs collection by enabling ContainerInsignts.  
### Traffic Search  
Traffic Search allows you to filter by source and destination VMs, flow types like Intra-VNet, Inter-Peered-VNets, Azure-owned PIPs and external PIPs.
This gives you valuable network traffic insights to your environment.  
The data is based on "NetworkMonitoring" and "AzureNetworkAnalytics_CL" Log Analytics tables created when you enable Network Performance Monitoring and Traffic Analytics. See [Collect Log](https://github.com/weixian-zhang/Panorama/blob/master/docs/SetupLogCollection.md).  
<img src="./docs/trafficsearch-1.png" width="800" height="500" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
<img src="./docs/trafficsearch-2.png" width="800" height="500" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
<img src="./docs/trafficsearch-3.png" width="800" height="500" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

### Inventory Dashboard
It contains 3 general categories:
* All Resources
* Virtual Machines: Number of Linux and Windows VMs and which VMs are running and which are not. Pie charts of VM grouped by Image Type and by VM SKU.
* Networking: All Virtual Networks and Subnets
  * Networking - NSG: whistleblowing which NSG has no rules,  
  Subnets with no NSG (excluding AzureFirewallSubnet and GatewaySubnet)  
  and which Inbound and/or Outbound rules has destination address * | Any | 0.0.0.0/0  
  
  * Networking - Public IP: Shows all resources with Public IPs and Public IPs not assiciated to any resource.
 
 ### Network Monitoring Guide
 This section provides a summary of the available Azure network monitoring tools and how to setup and use them.  
 Do check out a couple of great videos on entire [Azure Monitor landscape](https://www.youtube.com/watch?v=_MtrZOMQ18M) and another that covers [all current Azure networking tools](https://www.youtube.com/watch?v=3J97zMYhSCw). 

 * [Azure Load Balancer Insights](#azure-load-balancer-insights)
 * [Network Performance Monitor (NPM)](#network-performance-monitor-npm)
 * [Azure Monitor - Networks Insights](#azure-monitor---networks-insights)
 * [Traffic Analytics (NSG Flow logs)](#traffic-analytics-nsg-flow-logs)
 
 ---
 #### Azure Load Balancer Insights  
   What this does?  
   * Topology visuals of load balancer IP -> LB rule to backend-pool resources with colored link-lines to show traffic health
   * Availability: Backend pool health probe by backend VM IP addressa nd by Port. E.g: Backend VM can have healthy probes on port:80 but not port:443 due to no SSL cert setup.
   * Data Throughput: How much Megabytes is going through your Load Balancer by Frontend IP and Port
   * Flow Distribution:
     * Inbound: Total count of request/traffic coming into LB and distributed to each of the backend VM
     * Outbound: Total count of outbound request/traffic created by eech of your VM  
   
   References: [video](https://www.youtube.com/watch?v=qfzOTNKYTgU)  
 
 ---
 #### Network Performance Monitor (NPM)  
 
   What this does?  
   
   Focusing on 2 aspects of NPM (exclude ExpressRoute monitoring):  
   **Performance Monitoring** and **Service Connectivity Monitoring (SCM)**.<br />
   In a nutshell, NPM provides visual topology and info on VM to VM packet loss and latency(Performance Monitoring),  
   and Http-based SaaS/PaaS URL monitoring(SCM).<br /><br />
   * Performance Monitoring<br />
     MMA agents in each VM acting like a "health beacon" send health probe(synthetic transactions) packets via TCP/ICMP to each other several times to measure and capture info like latency and packet percentage loss. Few terms to figure out before one can effectively use NPM solution UI:  
      * Nodes: Actual VMs in subnets auto discovered from any VM with healthy MMA agent sending Heartbeat to workspace.
      * SUBNETWORKS: Actual subnets of a VNet. Subnetworks are auto discovered when Nodes are discovered, therefore Subnetworks can't be manually added unlike NETWORKS.
      * NETWORKS - This is similar to a VNet but its a logical network container for all discovered Subnetworks and can be any friendly name with spaces. Although Network could be a 1:1 to a VNet but it gives flexibility to group subnets in a another logical way apart from actual VNet.   
     
   * Service Connectivity Monitoring  
     The same MMA agent in this case triggers connectivity to test Http, Https, TCP endpoints similiar to Network Watcher - Connection Troubleshoot.  
     The use cases for SCM therefore are broad:
     * TCP test - SQL Server, MySQL, FTP, SSH, SFTP servers
     * Http/s test - VNet-Injectable-PaaS like API Management Premium, Integrated Service Environment, Azure Function(Http-triggered) running in Azure Kubernetes and more
     * Https test - Internet SaaS endpoints  
   
   References:  
   * [Configure NPM solution](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/network-performance-monitor#set-up-and-configure)
   * [Configure Performance Monitoring](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/network-performance-monitor-performance-monitor)
   * [Configure Service Connectivity Monitoring](https://docs.microsoft.com/en-us/azure/azure-monitor/insights/network-performance-monitor-service-connectivity)
   
   ---
   #### Azure Monitor - Networks Insights
   This feature gives you an overall plus drill-down view on all nerworking resources in your environment.  
   Below screenshot with navigation guiding on each feature.<br /><br />
   <img src="./docs/guides/guides-azmon-networks-overallview.png" width="750" height="450" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
   
   * Networks Insights - Load Balancer Dependency View<br />
     This feature is the same as [Load Balancer Insights](#azure-load-balancer-insights)
   
   * Networks Insights - Application Gateway Dependency View<br /><br />
     Key Metrics [explained](https://docs.microsoft.com/en-us/azure/application-gateway/application-gateway-metrics#timing-metrics)  
     (Backend connection time, Backend first and last byte response time, total time, client round trip time)  
     
     Click on Dependency View icon to go to Application Gateway Metrics
     <img src="./docs/guides/guides-azmon-networks-appgw-dependencyview.png" width="750" height="450" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
     
     <img src="./docs/guides/guides-azmon-networks-appgwmetrics.png" width="750" height="450" align="left" /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /> 

   
   ---
   #### Traffic Analytics (NSG Flow logs)<br />
   
   References:  
   * [What is Traffic Analytics](https://docs.microsoft.com/en-us/azure/network-watcher/traffic-analytics)
   * Traffics Analytics Table AzureNetworkAnalytics_CL [Schema](https://docs.microsoft.com/en-us/azure/network-watcher/traffic-analytics-schema#fields-used-in-traffic-analytics-schema) 
   


