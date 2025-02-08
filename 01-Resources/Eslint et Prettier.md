---
Owner: Jeremie Cyrille
tags:
  - Testing
Last edited time: 2024-08-05T11:24
---
# Installer ESlint et Prettier

```Bash
npm i eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-config-prettier --save-dev
```

# Configurer ESlint

Lancer `npx eslint --init` puis choisir `standard` comme convention de lint.

# Add Eslint worflow

Dans `.github/workflows/eslint.yml`

```YAML
# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.
# ESLint is a tool for identifying and reporting on patterns
# found in ECMAScript/JavaScript code.
# More details at https://github.com/eslint/eslint
# and https://eslint.org

name: ESLint

on:
  push:
    branches: [ "main" ]
  pull_request:
    # The branches below must be a subset of the branches above
    branches: [ "main" ]
  schedule:
    - cron: '20 11 * * 4'

jobs:
  eslint:
    name: Run eslint scanning
    runs-on: ubuntu-latest
    permissions:
      contents: read
      security-events: write
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Install ESLint
        run: |
          npm install eslint@8.21.0 eslint-config-prettier eslint-config-standard @typescript-eslint/eslint-plugin @typescript-eslint/parser
          npm install @microsoft/eslint-formatter-sarif@2.1.7
      - name: Run ESLint
        run: npx eslint .
          --config .eslintrc.json
          --ignore-path .eslintignore
          --ext .js,.ts
          --format @microsoft/eslint-formatter-sarif 
          --output-file eslint-results.sarif
        continue-on-error: true

      - name: Upload analysis results to GitHub
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: eslint-results.sarif
          wait-for-processing: true
```