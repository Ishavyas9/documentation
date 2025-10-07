---
id: hyperexecute-yaml-creation-for-playwright
title: HyperExecute YAML Creation for Playwright
sidebar_label: YAML Creation for Playwright
description: Discover the power of HyperExecute connected workflows and how testers or developers can leverage it for their daily autoamtion testing of their organization features.
keywords:
  - LambdaTest Hyperexecute
  - LambdaTest Hyperexecute help
  - LambdaTest Hyperexecute documentation
  - LambdaTest Projects
  - YAML Creation
  - Playwright
url: https://www.lambdatest.com/support/docs/hyperexecute-yaml-creation-for-playwright/
site_name: LambdaTest
slug: hyperexecute-yaml-creation-for-playwright/
---

<script type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify({
       "@context": "https://schema.org",
        "@type": "BreadcrumbList",
        "itemListElement": [{
          "@type": "ListItem",
          "position": 1,
          "name": "Home",
          "item": "https://www.lambdatest.com"
        },{
          "@type": "ListItem",
          "position": 2,
          "name": "Support",
          "item": "https://www.lambdatest.com/support/docs/"
        },{
          "@type": "ListItem",
          "position": 3,
          "name": "HyperExecute YAML Creation for Playwright",
          "item": "https://www.lambdatest.com/support/docs/hyperexecute-yaml-creation-for-playwright/"
        }]
      })
    }}
></script>
This guide outlines common use cases and solutions for configuring Playwright test executions on **LambdaTest HyperExecute**. It covers dependency management, environment setup, caching, reporting, and troubleshooting common issues.

## Q: How can private dependencies be accessed via a custom registry?
If your project uses private dependencies hosted on a custom registry, you must configure access before installing the packages. Add the following commands in the `pre` section of your YAML file:

```yaml title="hyperexecute.yaml"
pre:
  - npm config set registry <URL>
  - npm install
```

## Q: How can a specific Playwright project be executed?
When a project has multiple Playwright projects defined, it may be necessary to run a specific one. Using the `--project` flag ensures that only the intended project executes without affecting others. Check that your execution command includes `--project="PROJECTNAME"`and append it to the `testRunnerCommand`.

```javascript
npx playwright test --project=chromium
```

## Q: How can tests be executed with a specific configuration file?
For setups with multiple configuration files, specifying the correct config file during execution ensures that the intended environment and settings are applied, avoiding conflicts or unexpected behavior.

```javascript
npx playwright test --config=playwright.config.staging.ts
```

## Q: How can skipped tests be ignored during test discovery?
To ignore test cases marked with test.skip, create a custom Node.js script.

- Create a file named `discovery.js` and add the script from the [Gist](https://gist.github.com/mohitsaini28r/453368e52143fa43efa271b1511aa2e7).
- Update the `testDiscovery` block in your YAML:

```yaml title="hyperexecute.yaml"
testDiscovery:
  command: node discovery.js
```

## Q: How can private dependencies be accessed through a private network proxy?
When private dependencies require access through a private network, configure HTTP and HTTPS proxies.

**For npm:**

```yaml title="hyperexecute.yaml"
pre:
  - npm config set proxy http://${LT_PROXY_HOST}:${LT_PROXY_PORT}
  - npm config set https-proxy http://${LT_PROXY_HOST}:${LT_PROXY_PORT}
```

**For yarn:**

```yaml title="hyperexecute.yaml"
pre:
  - yarn config set proxy http://${LT_PROXY_HOST}:${LT_PROXY_PORT}
  - yarn config set https-proxy http://${LT_PROXY_HOST}:${LT_PROXY_PORT}
```

## Q: How can scripts be run on each machine after test execution?
Use the `post` parameter in the YAML file. Typical use cases include:

- Running cleanup scripts
- Closing API connections
- Uploading test results to tools like Report Portal or Zephyr

```yaml title="hyperexecute.yaml"
post:
  - ./scripts/cleanup.sh
  - ./scripts/upload-results.sh
```

## Q: How can tasks be executed after all test executions are complete?
Use the `globalPost` parameter to execute tasks once all tests have finished. You can run it on local or remote machines and configure caching if needed.

Common use cases:
- Merging reports
- Sending email notifications
- Posting summaries to APIs or services

```yaml title="hyperexecute.yaml"
globalPost:
  - ./scripts/merge-reports.sh
  - ./scripts/send-summary.sh
```

## Q: How can scripts be executed before all test executions start?
Use the `globalPre` parameter to prepare environments or generate config files.

Examples:
- Generate runtime files
- Import data
- Run preparatory commands

```yaml title="hyperexecute.yaml"
globalPre:
  - ./scripts/setup-env.sh
  - ./scripts/import-data.sh
```

## Q: How can smart caching be enabled in HyperExecute?
Caching dependencies improves efficiency by avoiding repeated installations. Using `cacheKey` and `cacheDirectories` in the YAML file enables caching for npm or Yarn, ensuring that dependencies are reused across executions.

**For npm:**

```yaml title="hyperexecute.yaml"
cacheKey: '{{ checksum "package-lock.json" }}'
cacheDirectories:
  - node_modules
```

**For yarn:**

```yaml title="hyperexecute.yaml"
cacheKey: '{{ checksum "yarn.lock" }}'
cacheDirectories:
  - node_modules
```

## Q: What is `testDiscovery` and how can it be configured?
`testDiscovery` identifies test files or methods to execute. It supports `raw` type with `static` or `dynamic` modes.

**File-level discovery:**

```yaml title="hyperexecute.yaml"
testDiscovery:
  type: raw
  mode: static
  command: grep -lr 'describe' tests
```

**Test-level discovery:**

```yaml title="hyperexecute.yaml"
testDiscovery:
  type: raw
  mode: dynamic
  command: grep -rn "test(" tests | cut -d: -f1,2
```

## Q: How can Playwright reports be configured in HyperExecute?
To generate and access Playwright HTML reports in HyperExecute, the reports must be stored in a known directory. The YAML file should include a `post` section to upload the directory as an artifact. Partial reports can be configured for framework-specific reporting.

- Update `playwright.config` to specify the report output location:

```javascript title="playwright.config"
reporter: [["html", { outputFolder: "playwright-report", open: "never" }]]
```

- Update `hyperexecute.yaml` file:

```yaml title="hyperexecute.yaml"
report: true
partialReports:
  frameworkName: playwright
  location: playwright-report
  type: HTML
```

## Q: How can tag-level discovery be performed in Playwright tests?
If tests include tags and only specific tags need to be executed, a custom Node.js script can be used for tag-based discovery. This allows filtering tests at the method level and executing only those matching the desired tag expression.

- Create a file named `discovery.js` at the root level of the project (in the same directory as package.json).
- Copy the script from the [Gist](https://gist.github.com/gauravchawhan/9568ed96d6bc115707d37f695a56a6e7) into that file.
- Update the testDiscovery section in your hyperexecute.yaml to run this script using the node command, and pass your desired tag expression.

```yaml title="hyperexecute.yaml"
testDiscovery:
  type: raw
  mode: static
  command: node discovery.js '(?=.*@PROD)(?=.*@LOGIN)'
```

## Q: Why do tests pass locally and on the automation grid but fail in HyperExecute?
This occurs due to a version mismatch between the Playwright client and server. In automation grid runs, the client is installed by the user, while the server is managed internally. In HyperExecute, both client and server must be explicitly installed and configured in the YAML to ensure compatibility.

- Verify the required Playwright version by checking the dependency listed in your `package.json` file.
- Once identified, install the specific version of Playwright during the pre step of the YAML:

```yaml title="hyperexecute.yaml"
pre:
  - npx playwright@1.41.0 install
```
> Replace `1.41.0` with the version specified in the project’s package.json.

## Q: Why are tests retried multiple times within a single scenario?
Multiple retries occur when retry logic is configured both at the Playwright framework level and in HyperExecute YAML. This can cause duplicate scenarios, incorrect reporting, and multiple executions of the same test. Disabling framework-level retries and using only HyperExecute-level retries avoids this problem.

```yaml title="hyperexecute.yaml"
retryOnFailure: true
maxRetries: 1
```

## Q: How can environment variables required for test execution be configured?
Certain frameworks or projects require specific environment variables, such as credentials or base URLs. Configuring these variables via the `env` section in the YAML or using a `.env` file ensures that tests execute successfully in HyperExecute.

```yaml title="hyperexecute.yaml"
env:
  BASE_URL: https://example.com
  API_KEY: your_api_key_here
```

```bash title=".env"
BASE_URL=https://example.com
API_KEY=your_api_key_here
```

## Q: Why can tasks get stuck due to reports opening on a local server?
Playwright tests may hang if the HTML report is configured to automatically open on a local server after execution. Since HyperExecute runs in a headless CI environment, attempting to open the report in a browser window causes the process to stall indefinitely.

To prevent this, update your `playwright.config.ts` file to prevent the report from opening automatically by setting the open option to `'never'`.

```javascript title=playwright.config.ts"
reporter: [['html', { open: 'never' }]]
```

## Q: Why might a dependency work locally but fail on HyperExecute?
Dependencies that work locally may fail in HyperExecute due to OS-specific `package-lock.json` or `yarn.lock` files. These lock files may prevent correct resolution on a different operating system. Deleting or ignoring these files ensures fresh dependency installation. To ignore these files before uploading the project, add them to the `.gitignore` or `.hyperexecuteignore` file

## Q: Why do unexpected `driver.quit` errors occur when running tests with parameters?
These errors can happen when there is a version mismatch between the Playwright server installed in HyperExecute and the client used in the project. Installing the exact version in the YAML prevents unstable or unexpected behavior.

For example, to install version `1.50.0`:

```yaml title="hyperexecute.yaml"
pre:
  - npx playwright@1.50.0 install
```

## Q: Why might the browser fail to launch on HyperExecute?
Tests may fail to start if required browser binaries are missing or not installed correctly. Installing all Playwright dependencies, including browsers, ensures successful test execution.

```yaml title="hyperexecute.yaml"
pre:
  - npx playwright install --with-deps
```

## Q: Why do tests time out on HyperExecute but pass locally?
Tests can time out due to differences in resource availability, execution speed, or default timeouts between local and HyperExecute environments. Increasing the timeout in the Playwright config or test file mitigates this issue.

```javascript
test.setTimeout(60000); // 60 seconds
```

## Q: Why do configuration files fail when using hardcoded absolute paths?
Absolute paths specific to a local environment may not exist in HyperExecute. Using relative paths from the project root ensures that scripts and configuration files remain portable across environments.

```javascript
// Instead of require("C:/user/folder/test.js")
require("./tests/test.js")
```

## Q: Why are screenshots or videos not available in artifacts?
If Playwright is not configured to capture screenshots, videos, or traces, or if these artifacts are not uploaded correctly from HyperExecute, they will not appear in the report. Correct configuration in both `playwright.config.ts` and YAML ensures artifacts are captured and visible.

- Update the `playwright.config.ts` file:
```javascript title="playwright.config.ts"
use: {
  screenshot: 'on',
  video: 'on',
  trace: 'on-first-retry',
}
```

- Update the `hyperexecute.yaml` file:
```yaml title="hyperexecute.yaml"
uploadArtefacts:
  - name: FinalReport
    path:
      - test-results/**
      - playwright-report/**
```

## Q: Why do "Cannot find module" errors occur during execution?
These errors occur when required modules are missing or the installation step is skipped. Ensuring that all dependencies listed in `package.json` are installed in the `pre` step of the YAML prevents this issue.

```yaml title="hyperexecute.yaml"
pre:
  - npm install
```