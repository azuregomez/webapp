# App Service with SQL DB 
## Why migrate your application to App Service and Azure SQL DB?
* Get out of the business of managing infrastructure. Just manage code and ship new features faster.
* Get built-in Cloud Native features: Monitoring, Autoscaling, High Availability, Disaster Recovery.
* App Service is the only managed app hosting platform for .net. 
* 2 decades of investment and 25+ years of SQL innovation.
* Proven success: hosting 2M apps and 41B daily requests with 99.95% SLA.
* Free App Service and Database Migration Assistants.
* Leverage full network security and integration, with internet traffic blocked, firewalls protecting your deployment and supporting hybrid applications that integrate securely with other services in your network.
## Technical Requirements of the solution presented
.net application migration with a SQL Server back end the following Security features:
* No public endpoints available for Web Application or SQL Database.
* Secrets like database connection strings not available in code or application configuration.
* Internal Web Application Firewall in front of Web Application to protect against the top 10 OWASP threats.
* Hybrid connectivity: Outbound traffic from the Web App to other VNet and on-premise resources.
## Architecture
![Landing Zone](https://github.com/azuregomez/webapp/blob/main/websql.png)
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

### Notes
Since Application Gateway V2 does not support only private IP mode, App Gateway is created with both public and private IP but no listeners are created for the public frontend IP address.\
An additional security feature would be to attach an NSG for the App Gateway subnet as explained here:\
https://docs.microsoft.com/en-us/azure/application-gateway/application-gateway-faq#how-do-i-use-application-gateway-v2-with-only-private-frontend-ip-address
