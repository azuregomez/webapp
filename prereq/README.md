# Landing Zone
This folder deploys a Landig Zone VNet:
Subnet | Purpose
------|--------
AzureBastionSubnet | Azure Bastion
dropboxSubnet | Dropbox VM to connect with bastion
wafSubnet | AppGateway WAF
appInboundSubnet | Private Endpoint for App Service
appOutboundSubnet | AppService VNet Integration - outbound connectvity to VNet
sqlSubnet | Private Endpoint for SQL DB
## Architecture
![Landing Zone](https://github.com/azuregomez/webapp/blob/main/prereq/lz.png)
