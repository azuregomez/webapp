# App Service with SQL DB 
## Architecture
![Landing Zone](blob/main/websql.png)
This architecture leverages the following Azure Security features:

Feature | Purpose | Reference
------- | ------- | -----
Key Vault | Store secrets like SQL connection string securely. | https://docs.microsoft.com/en-us/azure/key-vault/general/basic-concepts
Managed Identity |  App Service identity to securely access Key Vault secrets. | https://docs.microsoft.com/en-us/azure/app-service/overview-managed-identity
Private Endpoint for Web App | Eliminate exposure from the public internet. | https://docs.microsoft.com/en-us/azure/app-service/networking/private-endpoint
VNet Integration |  Enables apps to access resources in or through a VNet |  https://docs.microsoft.com/en-us/azure/app-service/web-sites-integrate-with-vnet
Private Endpoint for SQL DB |  Connect to SQL DB through a private IP | https://docs.microsoft.com/en-us/azure/azure-sql/database/private-endpoint-overview
SQL DB Firewall rules | Eliminate exposure from the public internet | https://docs.microsoft.com/en-us/azure/azure-sql/database/firewall-configure
App Gateway | Web Application Firewall  |   https://docs.microsoft.com/en-us/azure/architecture/example-scenario/gateway/firewall-application-gateway

