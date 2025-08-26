---
id: hyperexecute-yaml-version0.2
title: HyperExecute Yaml Version 0.2
hide_title: false
sidebar_label: HyperExecute Yaml Version 0.2
description: Learn more about HyperExecute YAML 0.2
keywords:
  - LambdaTest Hyperexecute
  - LambdaTest Hyperexecute help
  - LambdaTest Hyperexecute documentation
url: https://www.lambdatest.com/support/docs/hyperexecute-yaml-version0.2/
site_name: Hyperexecute Yaml Version 0.2
slug: hyperexecute-yaml-version0.2/
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
          "name": "Hyperexecute Yaml Version 0.2",
          "item": "https://www.lambdatest.com/support/docs/hyperexecute-yaml-version0.2"
        }]
      })
    }}
></script>
This version introduces several new features and improvements over Version 0.1. This documentation outlines the changes and provides guidance on when to use Version 0.2 instead of Version 0.1.

:::info
- Currently supported frameworks are **maven/testng**, **maven/junit4**, **maven/junit5**, **wdio/mocha**, and **wdio/jasmine** framework.
- Version 0.2 supports all the fields available in Version 0.1, except for [`testDiscovery`](/support/docs/deep-dive-into-hyperexecute-yaml/#testdiscovery) and [`testRunnerCommand`](/support/docs/deep-dive-into-hyperexecute-yaml/#testrunnercommand)
- The new [`framework`](/support/docs/hyperexecute-yaml-version0.2/#framework) flag has been introduced to configure the test framework.
:::

## Why to use HyperExecute YAML Version 0.2?

- The new framework feature supports caching by default. You do not have to specify any directories to cache for faster performance. If you adds the [`cacheKey`](/support/docs/deep-dive-into-hyperexecute-yaml/#cachekey) and [`cacheDirectories`](/support/docs/deep-dive-into-hyperexecute-yaml/#cachedirectories) keys in your yaml, the default caching gets disabled and preference is given to user specified cache.
- In Version 0.2, the support for [matrix mode](/support/docs/hyperexecute-matrix-multiplexing-strategy/) has been removed, and only [static discovery](/support/docs/deep-dive-into-hyperexecute-yaml/#mode) is available. This means that the discovery command will run on your system rather than in a matrix.
- Since the support for [`testRunnerCommand`](/support/docs/deep-dive-into-hyperexecute-yaml/#testrunnercommand) is removed, the test orchestration will be managed automatically.

## ```framework```

The ```framework``` field in Hyperexecute YAML Version 0.2 allows you to configure the test framework settings. It provides more flexibility and customization options for your testing needs with the following parameters.

| Parameters | Type | Mandatory | Description|
|:---|:--|:---|:---|
| [name](#name) | String | Yes | You need to specify which testing framework you are using in your repo.|
| [flags](#flags) | Array | No | Command line flags to pass to the custom runner for both test discovery and execution.|
| [discoveryFlags](#discoveryFlags) | Array | No | Command line flags to pass to the custom runner for test discovery only.|
| [runnerFlags](#runnerFlags) | Array | No | Command line flags to pass to the custom runner for test execution only. |
| [discoveryType](#discoveryType) | String | No | Specifies the type of test discovery to use. Supported values are "method" and "class". The default is "method".|
| [workingDirectory](#workingDirectory) | String | No | Specifies the working directory where all discovery and execution commands will be executed.|
| [defaultReports](#defaultReports) | Boolean | No | Specifies whether to create default reports for the specified framework.|
| [region](#region) | String | No | Specifies in which region you want to spin your appium tests.|
| [artifacts](#artifacts) | Boolean | No | Specifies whether to generate artifacts or not |
| [language](#language) | String | No | Specifies the device’s system language for the test session. This determines the language in which your app’s UI and strings will be displayed. |
| [locale](#locale) | String | No | Defines the regional format settings such as date, time, currency, and number conventions. |

### `name`
Specifies the testing framework used in your repository.

```yaml
framework:
  name: "maven/testng"
``` 

To enable maven runner with Appium, you have to pass `appium: true` before the `framework` field

```yaml
appium: true
framework: 
  name: "maven/testng"
```

### `flags`
Specifies the command line flags to pass to the custom runner for both test discovery and execution.

```yaml
framework:
  name: "maven/testng"
  flags: ["-Dplatname=win", "-Dgroups=selenium-test"]
```

### `discoveryFlags`
Specifies the command line flags to pass to the custom runner for test discovery only.

```yaml
framework:
  name: "maven/testng"
  discoveryFlags: ["-Dgroups=selenium-test"]
```

### `runnerFlags`
Specifies the command line flags to pass to the custom runner for test execution only.

```yaml
framework:
  name: "maven/testng"
  runnerFlags: ["-Dgroups=database"]
```

### `discoveryType`
Specifies the level at which user wants to discover the tests. Supported values are "method" and "class". The default is "method".

```yaml
framework:
  name: maven/testng
  #highlight-next-line
  discoveryType: method
  # instead of method you can also use xmltest or class as a discovery type
  flags:
    - "-Dplatname=win"
```
:::info
- For **maven/testng** the supported discovery types are **method, class** and **xmltest**. The default is **method**.
- For **maven/junit4** and **maven/junit5**  the supported discovery types are **method** and **class**. The default is **method**.
- For **wdio/mocha** and **wdio/jasmine** the supported discovery types are **test, spec, suite** and **wdiosuite**. The default is **spec**. 
:::

### `workingDirectory`
<!-- Specifies the working directory where all discovery and execution commands will be executed. -->

The `working directory` specifies the location of the directory in which all test discovery and execution commands will be run, as well as the location of any files or directories that are created as a result of the command execution.  If the `workingDirectory` option is not specified, then the working directory will be the directory where the YAML file is located.

```yaml
framework:
  name: maven/testng
  discoveryType: method
  workingDirectory: src/main
  flags:
    - "-Dplatname=win"
```

### `defaultReports`
Specifies whether to create default reports for the specified framework.

```yaml
framework:
  name: maven/testng
  defaultReports: false
  flags:
    - "-Dplatname=win"
```

### `region`

The region parameter specifies the region or location where the Appium tests will be executed. Our platform supports the following three regions:

- ap (Asia-Pacific)
- us (United States)
- eu (European Union)

> The region parameter should always be defined under the `args` parameter, as shown in the below sample code.

```yaml
framework:
  args:
    region: us
```

### `artifacts`

To generate artifacts for your Espresso tests, add the `artifacts: true` flag in your YAML file:

```yaml
framework:
  args:
    artifacts: true
```

> 📕 Learn [how to perform group-based test discovery in TestNG](/support/docs/hyperexecute-how-to-perform-group-based-test-discovery-in-testng)


### `language`

Specifies the device’s system language for the test session. This determines the language in which your app’s UI and strings will be displayed.

```yaml
framework:
  args:
    language: es
```

### `locale`

Defines the regional format settings such as date, time, currency, and number conventions.

```yaml
framework:
  args:
    locale: ES
```


## Sample Yaml Version 0.2

```yaml
---
version: 0.2
runson: win

autosplit: true
concurrency: 2

pre:
  # Skip execution of the tests in the pre step
  - mvn dependency:resolve

framework:
  name: maven/testng
  flags:
    - "-Dplatname=win"
  discoveryFlags: ["-Dgroups=selenium-test"]
  runnerFlags: ["-Dgroups=database"]
  discoveryType: method
  workingDirectory: src/main
  defaultReports: false
  args:
    region: ap
    language: es
    locale: es

retryOnFailure: true
maxRetries: 1

post:
  - ls target/surefire-reports/

mergeArtifacts: true
uploadArtefacts:
 - name: ExecutionSnapshots
   path:
    - target/surefire-reports/html/**
```