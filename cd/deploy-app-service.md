# Deploy Application App Service

## Jobs Deploy

```yaml
jobs:
  build-and-deploy-app-service:
    name: Build and Deploy
    runs-on: ubuntu-latest
    environment: env
    steps:
    .
    .
    .
```

### Steps for Deploy Contaner

- [Checkout pipelines](steps.md#checkout-pipelines)
- [Login via Azure CLI](steps.md#login-via-azure-cli)
- [Set subscription](steps.md#set-subscription)
- [Deploy to Azure Web App](steps.md#deploy-to-azure-webapp)
- [Set Web App Settings](steps.md#set-web-app-settings)

