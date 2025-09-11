---
id: hyperexecute-release-notes-3-0-1
title: Version 3.0.1
hide_title: false
sidebar_label: Version 3.0.1
description: Version 3.0.1
keywords:
  - LambdaTest Hyperexecute
  - LambdaTest Hyperexecute help
  - LambdaTest Hyperexecute documentation
  - FAQs
url: https://www.lambdatest.com/support/docs/hyperexecute-release-notes-3-0-1/
site_name: LambdaTest
slug: hyperexecute-release-notes-3-0-1/
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
          "item": "https://www.lambdatest.com/support/docs/hyperexecute-release-notes-3-0-1/"
        }]
      })
    }}
></script>
## Workflow Variables on HyperExecute
With Workflow Variables, you can now customize your workflow execution. This makes it easier to reuse the same workflow across multiple scenarios without editing YAML or creating duplicate workflows.

- **Workflow-level Variables :** Define reusable variables (e.g., ENVIRONMENT, BROWSER) while creating or editing workflows.
- **Default & Multiple Values :** Assign defaults or provide multiple values per variable.
- **Runtime Overrides :** Update variable values at run time without changing saved defaults.

> To learn more about Workflow Variables on HyperExecute, refer to our [detailed documentation](/support/docs/hyperexecute-workflows/#workflow-variables)