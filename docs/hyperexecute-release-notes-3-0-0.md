---
id: hyperexecute-release-notes-3-0-0
title: Version 3.0.0
hide_title: false
sidebar_label: Version 3.0.0
description: Version 3.0.0
keywords:
  - LambdaTest Hyperexecute
  - LambdaTest Hyperexecute help
  - LambdaTest Hyperexecute documentation
  - FAQs
url: https://www.lambdatest.com/support/docs/hyperexecute-release-notes-3-0-0/
site_name: LambdaTest
slug: hyperexecute-release-notes-3-0-0/
---

import NewReleaseTag from '../src/component/newRelease.js';
import EnhancementTag from '../src/component/enhancementTag';
import BugFixTag from '../src/component/bugFixTag';
import CodeBlock from '@theme/CodeBlock';
import {YOUR_LAMBDATEST_USERNAME, YOUR_LAMBDATEST_ACCESS_KEY} from "@site/src/component/keys";

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
          "name": "Version",
          "item": "https://www.lambdatest.com/support/docs/hyperexecute-release-notes-3-0-0/"
        }]
      })
    }}
></script>
## Language Support for Android Real Device Maestro Framework

We have introduced language support for Maestro tests on Android devices in HyperExecute. Now, you can configure the language parameter directly in your HyperExecute YAML under the [framework](https://www.lambdatest.com/support/docs/hyperexecute-yaml-version0.2/#framework) flag.

This enhancement is particularly useful when your testing applications in non-English environments. For example, you can now run tests in Spanish by setting:

```yaml title="hyperexecute.yaml"
framework:
  name: raw
  args:
    language: es
    locale: ES
```

## BiDi Testing Support with Selenium WebDriver
HyperExecute now supports BiDi (Bi-Directional) Testing with Selenium WebDriver. BiDi provides a two-way communication channel between the client and the browser, allowing you to go beyond traditional WebDriver commands. With BiDi enabled, you can interact with real-time browser events such as console logs, network traffic, JavaScript exceptions, and more, all directly from your test scripts.

> To learn more about BiDi testing with Selenium WebDriver on HyperExecute, refer to our [detailed documentation](https://www.lambdatest.com/support/docs/hyperexecute-bidi-testing/)