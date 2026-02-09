# actions

Reusable GitHub actions to be used across Intellegens repos

## Available Actions

Below is a list of reusable GitHub Actions provided in this repository, including their input parameters and usage examples.

---

### 1. Publish SARIF results to GitHub

**Path:** `.github/actions/dotnet-sarif-to-md`

Publishes SARIF results from .NET code analysis to GitHub Actions as annotations and summary markdown.

**Inputs:**

- `report-path` (required, default: `./`): Path to SARIF report file (e.g., `./report/`)
- `report-name` (required, default: `dotnet_report.sarif`): Full report name (e.g., `dotnet_report.sarif`)
- `report-title` (optional, default: `report-sarif`): Name for the report artifact

**Usage:**

```yaml
- uses: intellegens-hr/actions/.github/actions/dotnet-sarif-to-md@main
  with:
    report-path: ./build/
    report-name: results.sarif
    report-title: my-sarif-report
```

---

### 2. Dotnet Format Report Summary

**Path:** `bin/actions/dotnet-sarif-md`

Parses a dotnet-format SARIF/JSON report, generates a markdown summary, and can fail the workflow on warnings/errors.

**Inputs:**

- `report-path` (required, default: `report.sarif`): Path or glob pattern to the report file
- `fail-on-warning` (optional, default: `false`): Fail workflow on warnings
- `fail-on-error` (optional, default: `true`): Fail workflow on errors

**Usage:**

```yaml
- uses: intellegens-hr/actions/bin/actions/dotnet-sarif-md@main
  with:
    report-path: ./build/results.sarif
    fail-on-warning: true
    fail-on-error: true
```

---

### 3. .NET Build and Lint

**Path:** `.github/actions/dotnet-ci`

Installs dependencies, builds, sets up environment for .NET projects, and runs code analysis.

**Inputs:**

- `working-directory` (optional, default: `./`)
- `dotnet-version` (optional, default: `8.0.x`)
- `sln-file` (required): Path to solution file

**Usage:**

```yaml
- uses: intellegens-hr/actions/.github/actions/dotnet-ci@main
  with:
    working-directory: ./src/
    dotnet-version: 8.0.x
    sln-file: MySolution.sln
```

---

### 4. Setup Inspector Code tools and run code analysis

**Path:** `.github/actions/dotnet-lint-jb`

Sets up Inspector Code tools and runs code analysis for .NET projects.

**Inputs:**

- `working-directory` (optional, default: `./`)
- `sln-file` (required): Path to solution file

**Usage:**

```yaml
- uses: intellegens-hr/actions/.github/actions/dotnet-lint-jb@main
  with:
    working-directory: ./src/
    sln-file: MySolution.sln
```

---

### 5. .NET Prepare Environment and Build

**Path:** `.github/actions/dotnet-build`

Installs dependencies, builds, and sets up environment for .NET projects.

**Inputs:**

- `working-directory` (optional, default: `./`)
- `dotnet-version` (optional, default: `8.0.x`)

**Usage:**

```yaml
- uses: intellegens-hr/actions/.github/actions/dotnet-build@main
  with:
    working-directory: ./src/
    dotnet-version: 8.0.x
```

---

### 6. TypeScript Build and Lint

**Path:** `.github/actions/ts-ci`

Installs dependencies, builds, sets up environment for TypeScript projects, and runs ESLint and Prettier.

**Inputs:**

- `working-directory` (optional, default: `./`)
- `version` (optional, default: `10`)
- `eslint-fail-on-error` (optional, default: `false`)

**Usage:**

```yaml
- uses: intellegens-hr/actions/.github/actions/ts-ci@main
  with:
    working-directory: ./frontend/
    version: 10
    eslint-fail-on-error: true
```

---

### 7. TypeScript Prepare Environment and Build

**Path:** `.github/actions/ts-build`

Installs dependencies, builds, and sets up environment for TypeScript projects.

**Inputs:**

- `working-directory` (optional, default: `./`)
- `version` (optional, default: `10`)

**Usage:**

```yaml
- uses: intellegens-hr/actions/.github/actions/ts-build@main
  with:
    working-directory: ./frontend/
    version: 10
```

---

### 8. Run ESLint for TypeScript projects

**Path:** `.github/actions/ts-eslint`

Runs ESLint and outputs results in JSON format for TypeScript projects.

**Inputs:**

- `working-directory` (optional, default: `./`)
- `report-name` (optional, default: `eslint_report.json`)
- `fail-on-error` (optional, default: `false`)

**Usage:**

```yaml
- uses: intellegens-hr/actions/.github/actions/ts-eslint@main
  with:
    working-directory: ./frontend/
    report-name: eslint_report.json
    fail-on-error: true
```

---

### 9. Run Prettier for TypeScript projects

**Path:** `.github/actions/ts-prettier`

Runs Prettier and outputs results to GitHub Action summary for TypeScript projects.

**Inputs:**

- `working-directory` (optional, default: `./`)
- `fail-on-error` (optional, default: `false`)

**Usage:**

```yaml
- uses: intellegens-hr/actions/.github/actions/ts-prettier@main
  with:
    working-directory: ./frontend/
```

---

> For each action, adjust the `uses:` path and input values as needed for your project. See action YAML files for more details.
