# Steps in Jobs

## Checkout Code

```yaml
jobs:
  jobname:
    name: name
    runs-on: host
    environment: env
    steps:
    - name: Checkout code
      uses: actions/checkout@v2
```

## Setup Golang

```yaml
jobs:
  jobname:
    name: name
    runs-on: host
    environment: env
    steps:
    - name: Setup go
      uses: actions/setup-go@v2
      with:
        go-version: '^1.17.6' # The Go version to download (if necessary) and use.
```

## Check Go Version

```yaml
jobs:
  jobname:
    name: name
    runs-on: host
    environment: env
    steps:
    - run: |
        go version
```

## Install Go dependencies

```yaml
jobs:
  jobname:
    name: name
    runs-on: host
    environment: env
    steps:
    - name: Install dependencies
      run: |
        go env -w GO111MODULE=on
        go get -u github.com/gin-gonic/gin
        go get -u go.mongodb.org/mongo-driver/mongo
        go get -u github.com/stretchr/testify
        go mod vendor
```

## Unit test with Go

```yaml
jobs:
  jobname:
    name: name
    runs-on: host
    environment: env
    steps:
    - name: Unit test
      run: |
        go test -coverprofile coverage.out ./...
        go tool cover -html coverage.out -o report.html
```

## Upload Reports

```yaml
jobs:
  jobname:
    name: name
    runs-on: host
    environment: env
    steps:
    - name: Upload Reports
      uses: actions/upload-artifact@v2
      with:
        name: Unit Test Results
        path: '${{ github.workspace }}/report.html'
```


