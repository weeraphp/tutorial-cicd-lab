# Steps in Jobs

## Checkout Code

```yaml
steps:
- name: Checkout code
  uses: actions/checkout@v2
```

## Setup Golang

```yaml
steps:
- name: Setup go
  uses: actions/setup-go@v2
  with:
    go-version: '^1.17.6' # The Go version to download (if necessary) and use.
```

## Setup Node

```yaml
steps:
- name: Setup node
  uses: actions/setup-node@v2
  with:
    node-version: '14'
```


## Check Go Version

```yaml
steps:
- run: |
    go version
```

## Install Go dependencies

```yaml
steps:
- name: Install dependencies
  run: |
    go env -w GO111MODULE=on
    go get -u github.com/gin-gonic/gin
    go get -u go.mongodb.org/mongo-driver/mongo
    go get -u github.com/stretchr/testify
    go mod vendor
```
## Install Node dependencies

```yaml
steps:
- name: Install dependencies
  run: npm install
```


## Unit test with Go

```yaml
steps:
- name: Unit test
  run: |
    go test -coverprofile coverage.out ./...
    go tool cover -html coverage.out -o report.html
```

## Unit test with Node Jest

```yaml
steps:
- name: Unit test
  run: npm test
  # for vuejs npm run test:unit
```


## Upload Reports Go Report

```yaml
steps:
- name: Upload Reports
  uses: actions/upload-artifact@v2
  with:
    name: Unit Test Results
    path: '${{ github.workspace }}/report.html'
```

## Upload Reports Node Report Jest

```yaml
steps:
- name: Upload Reports
  uses: actions/upload-artifact@v2
  with:
    name: Unit Test Results
    path: '${{ github.workspace }}/coverage/lcov-report/*'
```


## Initialize CodeQL

```yaml
steps:
# Initializes the CodeQL tools for scanning.
- name: Initialize CodeQL
  uses: github/codeql-action/init@v1
  with:
    languages: ${{ matrix.language }}
    # If you wish to specify custom queries, you can do so here or in a config file.
    # By default, queries listed here will override any specified in a config file.
    # Prefix the list here with "+" to use these queries and those in the config file.
    # queries: ./path/to/local/query, your-org/your-repo/queries@main
```

## Autobuild CodeQL

```yaml
steps:
# Autobuild attempts to build any compiled languages  (C/C++, C#, or Java).
# If this step fails, then you should remove it and run the build manually (see below)
- name: Autobuild
  uses: github/codeql-action/autobuild@v1

# ℹ️ Command-line programs to run using the OS shell.
# 📚 https://git.io/JvXDl

# ✏️ If the Autobuild fails above, remove it and uncomment the following three lines
#    and modify them (or add more) to build your code if your project
#    uses a compiled language

#- run: |
#   make bootstrap
#   make release
```

## Perform CodeQL Analysis

```yaml
steps:
- name: Perform CodeQL Analysis
  uses: github/codeql-action/analyze@v1
```


## Build Image

```yaml
steps:
- name: Build image
  id: docker_build
  uses: docker/build-push-action@v2
  with:
    context: .
    tags: ${{ env.CONTAINER_REPOSITORY }}/${{ env.APP_NAME }}:${{env.IMAGE_TAG}}
```

## Login ACR

```yaml
steps:
- name: "ACR login"
  uses: azure/docker-login@v1
  with:
    login-server: ${{ env.CONTAINER_REPOSITORY }}
    username: ${{ secrets.ACR_USERNAME }}
    password: ${{ secrets.ACR_PASSWORD }}
```


## Push Image

```yaml
steps:
- name: Push image
  run: docker image push ${{ env.CONTAINER_REPOSITORY }}/${{ env.APP_NAME }}:${{env.IMAGE_TAG}}
```

## Repository Dispatch

```yaml
steps:
- name: Repository Dispatch
  uses: peter-evans/repository-dispatch@v1
  with:
    token: ${{ secrets.REPO_ACCESS_TOKEN }}
    repository: username/[name]-tutorial-pipeline
    event-type: name-tutorial-backend-cd-dev
    client-payload: '{"ref": "${{ github.ref }}", "sha": "${{ github.sha }}"}'
```

## Set Env

```yaml
steps:
- name: Set env
      run: echo "IMAGE_TAG=${GITHUB_REF#refs/*/}" >> $GITHUB_ENV
```