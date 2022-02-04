# Common Commponent

## Define Name

```yaml
name: DEV - Build
```

## Event Triggering

on env dev
```yaml
on:
  workflow_dispatch:
  
  push:
    branches:
      - develop
  pull_request:
    branches:
      - develop
```

on env sit
```yaml
on:
  push:
    tags:
      - '*'
```

## Environment Variables

on env dev

```yaml
env:
  APP_NAME: [name]-tutorial-frontend
  CONTAINER_REPOSITORY: "acr[name]tutorial001.azurecr.io"
  IMAGE_TAG: "0.0.1-SNAPSHOT"
```

on env sit

```yaml
env:
  APP_NAME: [name]-tutorial-frontend
  CONTAINER_REPOSITORY: "acr[name]tutorial001.azurecr.io"
```

