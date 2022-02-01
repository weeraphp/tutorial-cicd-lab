# Build Job

## Build Container Job

```yaml
build:
    name: Build
    runs-on: ubuntu-latest
    environment: 
      name: env
      url: https://github.com/[name]/[name]-tutorial-pipeline/actions/workflows/dev-tutorial-backend-deploy.yml
    needs: [unitest,analyze]
    steps:
    .
    .
    .
```

### Steps for Container Build

- [Checkout Code](steps.md#checkout-code)
- [Build Image](steps.md#build-image)
- [Login ACR](steps.md#login-acr)
- [Push Image](steps.md#push-image)
- [Repository Dispatch](steps.md#repository-dispatch)


## Build for Code Job

```yaml
repo-dispatch:
    name: Repository Dispatch
    runs-on: ubuntu-latest
    needs: [unitest,analyze]
    steps:
    .
    .
    .
```

### Steps for Code

- [Repository Dispatch](steps.md#repository-dispatch)



