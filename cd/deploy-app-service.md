# Deploy Application App Service

## Jobs Deploy

```yaml
jobs:
  build-and-deploy-app-service:
    name: Build and Deploy
    runs-on: ubuntu-latest
    environment: ${{ github.event_name == 'repository_dispatch' && 'dev' || github.event.inputs.env }}
    steps:
    .
    .
    .
```

### Steps for Deploy Contaner

- [Checkout pipelines]()
- [Checkout project]()
- [List working directory]()
- [Login via Azure CLI]()
- [Set subscription]()
- [Deploy to Azure Web App]()
- [Set Web App Settings]()

