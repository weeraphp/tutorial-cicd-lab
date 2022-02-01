# Unit Test Job

## Unitest Common Job

```yaml
unitest:
    name: UnitTest
    runs-on: ubuntu-latest
    environment: env
    steps:
    .
    .
    .
```

## Steps for Golang (Go test)

- [Checkout Code](steps.md#checkout-code)
- [Setup Go](steps.md#setup-golang)
- [Run](steps.md#check-go-version)
- [Install Dependencies](steps.md#install-go-dependencies)
- [Unittest](steps.md#unit-test-with-go)
- [Upload Report](steps.md#upload-reports-go-report)



## Steps NodeJS (with Jest)

- [Checkout Code](steps.md#checkout-code)
- [Setup Go](steps.md#setup-node)
- [Install Dependencies](steps.md#install-node-dependencies)
- [Unittest](steps.md#unit-test-with-node-jest)
- [Upload Report](steps.md#upload-reports-node-jest)



