# Common CI Workflows

## On Environment DEV

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
  APP_NAME: [name]-tutorial-frontend
#   for container build
  CONTAINER_REPOSITORY: "acr[name]tutorial001.azurecr.io"
  IMAGE_TAG: "0.0.1-SNAPSHOT"
```

## On Environment SIT / UAT / PRD

### Name

```yaml
name: SIT - Build
```

### Event Triggering

```yaml
on:
  push:
    tags:
      - '*'
```

### Env Variable

```yaml
env:
  APP_NAME: [name]-tutorial-frontend
#   for container build
  CONTAINER_REPOSITORY: "acr[name]tutorial001.azurecr.io"
  IMAGE_TAG: "0.0.1-SNAPSHOT"
```

