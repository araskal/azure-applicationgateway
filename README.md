# Using VM-Series Firewalls and the Azure Application Gateway to Secure Internet-Facing Web Workloads
This ARM template deploys a single VM-Series firewall between a pair of Azure load balancers. The external load balancer is an Azure Application Gateway (a web load balancer) that also serves as the Internet facing gateway, which receives traffic and distributes it to the VM-series firewall. The firewall enforces security policies to protect your workloads, and send the allowed traffic to the internal load balancer which is an Azure Load Balancer (Layer 4) that load balances across a pair of Windows Server 2016 Servers which are bootstrapped to load IIS. A second Azure Load Balancer (Layer 4) distributes traffic to a Sophos XG Firewall. The firewall enforces security policies to protect your internal workloads, and send the allowed traffic to the internal load balancer which is an Azure Load Balancer (Layer 4), splitting traffic into several subnets (DB, File, AD, Log).

As demand for your web services increase, you can add more servers and deploy additional firewalls for more capacity. Each tier, the VM-Series firewalls, web servers, Sophos XG Firewall, AD, File, Log and DB, are deployed in separate Availability Sets for higher availability and redundancy against planned and unplanned outages. Refer to Azure documentation for more information on [Availability Sets](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-linux-manage-availability). The configuration file for the Palo-Alto V-Series firewall and the Sophos XG Firewall is included.

**Support Policy**

***Supported***
 
This project is a fork of the Palo-Alto VM-Series azure deployment, customised for InLogik.
 
**Documentation**
* Release Notes: Included in this repository.
* Technical Documentation:[VM-Series Deployment Guide](https://www.paloaltonetworks.com/documentation/71/virtualization/virtualization/set-up-the-vm-series-firewall-in-azure/deploy-the-vm-series-and-azure-application-gateway-template.html)
* About the [VM-Series Firewall for Azure](https://azure.paloaltonetworks.com)

[<img src="http://azuredeploy.net/deploybutton.png"/>](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Faraskal%2Fazure-applicationgateway%2Fmaster%2Fazuredeploy.json)