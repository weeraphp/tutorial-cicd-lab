# Common CD Workflows

## On Environment DEV

### Name

```yaml
name: DEV - Build
```

### Event Triggering

```yaml
name: DEV - Tutorial Frontend Deploy
on:
  repository_dispatch:
    types: [bokie-tutorial-cd-appservice-dev]
  workflow_dispatch:
    inputs:
      env:
        description: "Environment"
        required: true
        default: "dev"
      ref:
        description: "Repository branch or tag"
        required: true
        default: "develop"
```


### Env Variable

```yaml
env:
  REPOSITORY: "tarathep/bokie-tutorial-frontend"
  APP_NAME: bokie-tutorial-frontend
  CONTAINER_REPOSITORY: "acrbokietutorial001.azurecr.io"
  IMAGE_TAG: "0.0.1-SNAPSHOT"
  GITREF: ${{ github.event_name == 'repository_dispatch' && 'develop' || github.event.inputs.ref }}
```

## On Enviroment SIT ,UAT ,PRD

### Name

```yaml
name: SIT - Build
```

### Event Triggering

```yaml
name: SIT - Tutorial Frontend Deploy
oon:
  workflow_dispatch:
    inputs:
      ref:
        description: Repository branch or tag
        required: true
        default: '0.0.1'
```


### Env Variable

```yaml
env:
  REPOSITORY: "tarathep/bokie-tutorial-frontend"
  APP_NAME: bokie-tutorial-frontend
  CONTAINER_REPOSITORY: "acrbokietutorial001.azurecr.io"
  IMAGE_TAG: ${{ github.event.inputs.ref }}
  GITREF: ${{ github.event_name == 'repository_dispatch' && 'main' || github.event.inputs.ref }}
  
```

