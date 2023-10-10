# Create a Service Principal:
```bash
az ad sp create-for-rbac --name spn-azure-bicep-github --role contributor --scopes /subscriptions/<SUBSCRIPTION_ID> --sdk-auth
```

# Deploy Bicep template using Azure CLI

## create resource group
```bash
az group create --name rg-bicep-webapp-013 --location westeurope
```

## preview changes
```bash
az deployment group what-if --resource-group rg-bicep-webapp-013 \
   --template-file webapp-linux.bicep \
   --parameters webAppName='bicep-013'
```
## deploy the web app using Bicep
```bash
az deployment group create --resource-group rg-bicep-webapp-013 \
   --template-file webapp-linux.bicep \
   --parameters webAppName='bicep-013'
```

