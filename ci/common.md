# Common CI Workflows

### Name

```yaml
name: DEV - Build
```

### Event Triggering

```yaml
on:
  workflow_dispatch:
  
  push:
    branches:
      - branch
  pull_request:
    branches:
      - branch

```

### Env Variable

```yaml
env:
  APP_NAME: [name]-tutorial-backend
#   for container build
  CONTAINER_REPOSITORY: "acr[name]tutorial001.azurecr.io"
  IMAGE_TAG: "0.0.1-SNAPSHOT"
```