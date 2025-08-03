# Azure App Service Deployment using Bicep and Azure DevOps

This project deploys an **App Service Plan** and an **App Service** (Web App) to Azure using **Bicep** and a **parameter file**. Deployment is triggered via an Azure DevOps pipeline.

---

## Project Structure
```plaintext
.
├── app_service.bicep         # Main Bicep template
├── uksouth-devops.bicepparam  # Parameter file
├── uksouth-github.bicepparam
├── azure-pipelines.yml       # Azure DevOps pipeline definition (optional)
└── README.md

---

## Resources Deployed

### 1. **App Service Plan**
- **Resource Type**: 'Microsoft.Web/serverfarms'
- **Name**: 'asp-{project_name}'
- **SKU**: 'F1' (Free) by default
- **Kind**: 'Linux' by default
- **Region**: Set via 'location' parameter

### 2. **App Service (Web App)**
- **Resource Type**: 'Microsoft.Web/sites'
- **Name**: 'app-{project_name}'
- **Region**: Same as App Service Plan
- **Linked to**: App Service Plan

---

## Parameters

Defined in the Bicep file:

| Name         | Type   | Default | Description                     |
|--------------|--------|---------|---------------------------------|
| 'kind'       | string | Linux   | OS type for App Service Plan    |
| 'location'   | string | —       | Azure region for deployment     |
| 'project_name' | string | —     | Base name for resources         |
| 'sku_name'   | string | F1      | App Service Plan SKU name       |
| 'sku_tier'   | string | Free    | App Service Plan tier           |

Example parameter file: 'app_service.parameters.bicepparam'

```bicep
using 'app_service.bicep'

param location = 'uksouth'
param project_name = 'app-service-uksouth'