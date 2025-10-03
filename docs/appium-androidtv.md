---
id: appium-androidtv
title: Android TV Automation
sidebar_label: Android TV
description: Learn how to automate Android TV apps using Appium with a step-by-step tutorial and sample Python code.
keywords:
  - android tv
  - appium
  - automation
  - androidtv
  - nvidia shield
  - python
url: https://www.lambdatest.com/support/docs/appium-androidtv
site_name: LambdaTest Docs
slug: appium-androidtv

---

import CodeBlock from '@theme/CodeBlock';
import {YOUR_LAMBDATEST_USERNAME, YOUR_LAMBDATEST_ACCESS_KEY} from "@site/src/component/keys";

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

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
          "name": "Apple TV With Appium",
          "item": "https://www.lambdatest.com/support/docs/appium-appletv/"
        }]
      })
    }}
></script>
## Tutorial To Run Your First Test On LambdaTest
---
As smart TVs continue to grow in popularity, relying solely on manual testing is no longer sufficient. Automating Android TV testing provides broader device coverage, enhances user experience by validating remote-based navigation and voice commands, and eliminates repetitive manual tasks. It also helps uncover issues earlier in the development cycle, ensuring a smooth and consistent experience across different Android TV models. 
In this guide, you will learn how to set up and run your **Android TV** automation testing scripts with **Appium** on the **LambdaTest Real Device Cloud platform**.

> To enable it for your organization, please contact us via <span className="doc__lt" onClick={() => window.openLTChatWidget()}>**24×7 chat support**</span> or you can also drop a mail to **support@lambdatest.com**.<br /> 

## Objective
---
By the end of this topic, you will be able to:

1.  Set up an environment for testing your Apps using **Android TV** with **Appium**.
2.  Understand and configure the core capabilities required for your Appium test suite.
3.  Explore the advanced features of LambdaTest.

## Prerequisites

---

Before you can start performing App automation testing with Appium, you would need to follow these steps:

- You have access to LambdaTest username and accessKey. If you have not registered yet, you can do the same by visiting our [website](https://accounts.lambdatest.com/register). You will be able to access the credentials in the [LambdaTest Profile](https://accounts.lambdatest.com/detail/profile)
- Install the latest Python build from the [official website](https://www.python.org/downloads/). We recommend using the latest version.
- Make sure **pip** is installed in your system. You can install **pip** from [pip documentation](https://pip.pypa.io/en/stable/installation/).

---
## Supported Models

| Device Model          | Platform Version |
|----------------------|------------------|
| Nvidia Shield TV      | Android 11       |

## Run Your First Test
---
### 1. Upload your application
Upload your **Android TV** application (.ipa file) to the LambdaTest servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

 **Using App File from System:**
 <div className="lambdatest__codeblock">
<CodeBlock className="language-bash">
{`curl -u "undefined:undefined" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/android-tv-sample-app.apk"" -F "name="androidtv_app" -F "type="androidtv""
`}
</CodeBlock>
</div>


### 2. Set Up Authentication

Make sure you have your LambdaTest credentials with you to run test automation scripts on LambdaTest. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans) or access the [Automation Dashboard](https://appautomation.lambdatest.com/). Then, set LambdaTest `Username` and `Access Key` in environment variables with following commands.

<Tabs className="docs__val">

<TabItem value="bash" label="Linux / MacOS" default>
  <div className="lambdatest__codeblock">
  <CodeBlock className="language-bash">
  {`export LT_USERNAME=${ YOUR_LAMBDATEST_USERNAME()} \\
export LT_ACCESS_KEY=${ YOUR_LAMBDATEST_ACCESS_KEY()}`}
</CodeBlock>
</div>

</TabItem>

<TabItem value="powershell" label="Windows" default>

  <div className="lambdatest__codeblock">
  <CodeBlock className="language-powershell">
  {`set LT_USERNAME=${ YOUR_LAMBDATEST_USERNAME()} \`
set LT_ACCESS_KEY=${ YOUR_LAMBDATEST_ACCESS_KEY()}`}
</CodeBlock>
</div>

</TabItem>
</Tabs>

### 3. Configure Desired Capabilities

In your automation script, set up the **platform capability** to specify that you are testing on an Android TV device.

<Tabs>
<TabItem value="Python" label="Python" default>

```python
   desired_caps = {
       "deviceName" : "Nvidia Shield TV",
       "platformVersion" :  "11",
        #highlight-next-line
       "platform" : "androidtv",
       "isRealMobile":True,
       "build": "Android TV Testing",
       "app":"APP_URL",     # Enter app url here
        "network": False,
       "geoLocation": "FR",
       "devicelog": True,
       "privateCloud": True, # For private cloud testing
       "visual" : True,
       "autoGrantPermissions": True

   }
```

</TabItem>
</Tabs>

## Additional Links

---

- [Advanced Configuration for Capabilities](https://www.lambdatest.com/support/docs/desired-capabilities-in-appium/)
- [How to test locally hosted apps](https://www.lambdatest.com/support/docs/testing-locally-hosted-pages/)
- [How to integrate LambdaTest with CI/CD](https://www.lambdatest.com/support/docs/integrations-with-ci-cd-tools/)

<nav aria-label="breadcrumbs">
  <ul className="breadcrumbs">
    <li className="breadcrumbs__item">
      <a className="breadcrumbs__link" target="_self" href="https://www.lambdatest.com">
        Home
      </a>
    </li>
    <li className="breadcrumbs__item">
      <a className="breadcrumbs__link" target="_self" href="https://www.lambdatest.com/support/docs/">
        Support
      </a>
    </li>
    <li className="breadcrumbs__item breadcrumbs__item--active">
      <span className="breadcrumbs__link">
      Roku TV With Appium
</span>
    </li>
  </ul>
</nav>



