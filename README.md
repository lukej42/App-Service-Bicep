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