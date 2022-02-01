# SAST Job

## SAST Job with CodeQL

```yaml
analyze:
    name: SAST CodeQL
    runs-on: ubuntu-latest
    permissions:
      actions: read
      contents: read
      security-events: write

    strategy:
      fail-fast: false
      matrix:
        language: [ '?' ]
        # CodeQL supports [ 'cpp', 'csharp', 'go', 'java', 'javascript', 'python' ]
        # Learn more:
        # https://docs.github.com/en/free-pro-team@latest/github/finding-security-vulnerabilities-and-errors-in-your-code/configuring-code-scanning#changing-the-languages-that-are-analyzed

    steps:
    .
    .
    .
```

## Steps for CodeQL

- [Checkout Code](steps.md#checkout-code)
- [Initialize CodeQL](steps.md#initialize-codeql)
- [Autobuild CodeQL](steps.md#autobuild-codeql)
- [Perform CodeQL Analysis](steps.md#perform-codeql-analysis)
