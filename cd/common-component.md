# Common Commponent

## Define Name

```yaml
name: ENV - Tutorial Frontend Deploy
```

## Event Triggering

on env dev
```yaml
on:
  repository_dispatch:
    types: [[name]-tutorial-frontend-cd-dev]
  workflow_dispatch:
```

on env sit
```yaml
on:
  workflow_dispatch:
    inputs:
      ref:
        description: "Image Tag"
        required: true
        default: "0.0.1"
```

## Environment Variables

on env dev

```yaml
env:
  REPOSITORY: "[username]/[name]-tutorial-frontend"
  APP_NAME: [name]-tutorial-frontend
  AZURE_WEB_APP_NAME: app-[name]-tutorial-frontend-dev-001
  CONTAINER_REPOSITORY: "acr[name]tutorial001.azurecr.io"
  IMAGE_TAG: "0.0.1-SNAPSHOT"
```

on env sit

```yaml
env:
  REPOSITORY: "[username]/[name]-tutorial-frontend"
  APP_NAME: [name]-tutorial-frontend
  AZURE_WEB_APP_NAME: app-[name]-tutorial-frontend-sit-001
  CONTAINER_REPOSITORY: "acr[name]tutorial001.azurecr.io"
  IMAGE_TAG: ${{ github.event.inputs.ref }}  
```

