---
id: appium-upload-media
title: Upload File and Media
hide_title: true
sidebar_label: Upload Files and Media
description: Seamlessly upload media and files on Real Devices to enhance your testing scenarios and ensure comprehensive validation of your application's functionalities.
keywords:
  - files upload
  - app test automation
  - media upload
  - upload automate
  - framework on lambdatest
  - app testing appium
  - app testing
  - real devices
url: https://www.lambdatest.com/support/docs/uploadMedia/
site_name: LambdaTest
slug: upload-media/
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
          "name": "Camera Image Injection",
          "item": "https://www.lambdatest.com/support/docs/uploadFileMedia/"
        }]
      })
    }}
></script>

# Uploading Files and Media on Real Devices

LambdaTest's file upload feature provides a convenient way to enhance your testing scenarios by allowing you to upload various media and non-media files directly to LambdaTest's cloud devices. In this section, we'll guide you through the process of uploading files, highlight the supported file types, and explain how to use `uploadMedia` capability while running your test scripts.

## Objectives
By the end of this topic, you will be able to:

1. Use Upload File and Media feature in Manual App testing.
2. Use Upload File and Media feature in App Automation.

-----

## Upload File and Media in Real Devices App Testing

Easily upload media or non-media files onto real devices during active sessions, enhancing your testing capabilities on LambdaTest's platform.

### Steps to Upload Files and Media Feature

1. Go to **App Testing** under the **Real Devices** section provided in the sidebar of your LambdaTest console.

2. Once the session is started, locate the toolbar and find the **Files and Media** option. 

<img loading="lazy" src={require('../assets/images/app-automation/uploadmedia.png').default} alt="Image" width="1200" height="550" className="doc_img"/>

  
3. You can now upload images, videos and files from your local on the device by clicking on the **Upload** button.

4. After the upload is completed, you can find the uploaded file or media in the specified `paths` mentioned below.


## File Storage Paths on Devices


| Category        | Platform | Location                                             | File Type      |
|-----------------|----------|------------------------------------------------------|----------------|
| Media Files     | Android  | Default gallery app, `/sdcard/Pictures`              | Images         |
|                 |          | Default gallery app, `/sdcard/Movies`                | Videos         |
|                 | iOS      | Camera Roll, `/private/var/mobile/Media/DCIM/`       | Images and Videos |
| Non-Media Files | Android  | Default Downloads folder of the device               | Files          |
|                 | iOS      | App’s directory: Files app → On My iPhone → Your app's directory | Files          |

### Supported File Types

LambdaTest supports various file types for upload, ensuring flexibility in your testing scenarios. Below are the supported file types:

- **Images**: JPG, JPEG, PNG, GIF (Maximum size: 10 MB)
- **Videos**: MP4  (Maximum size: 50 MB)
- **Files**: XLS, XLSX, DOC, DOCX, PDF, CSV, TXT (Maximum size: 15 MB)

## Upload File and Media feature in App Automation

This section provides a comprehensive guide on leveraging this feature within automation tests. It comprises two fundamental steps:

- Uploading the files and obtaining the `media_url`.
- Using `media_url` into your tests using `uploadMedia` capability.

### Step 1 : Uploading the files on Lambdatest Cloud

#### Using REST API

You can use the following curl command to upload any file `media` and `non-media` from your system to the LambdaTest cloud.

<div className="lambdatest__codeblock">
<CodeBlock className="language-bash">
{`curl --user "${YOUR_LAMBDATEST_USERNAME()}:${YOUR_LAMBDATEST_ACCESS_KEY()}" -X POST "https://api.lambdatest.com/mfs/v1.0/media/upload" -F "media_file=@"/Users/macuser/Downloads/image.jpeg"" -F "type=image" -F "custom_id=SampleImage"`
}
</CodeBlock>
</div>

**Request Parameters**
- `media_file`: This parameter denotes the media file to be uploaded from your local.
- `type`: This parameter denotes file type out of image,video and doc. 
- `custom_id`: This parameter specifies a custom identifier for the media file.

Below is a sample response demonstrating the return of the `media_url` parameter value:

```bash
{
    "media_url": "lt://MEDIAb48ab11c599944ee9dcd26b3e2978d3c",
    "name": "sample.csv",
    "status": "success",
    "custom_id": "Sample"
}
```
#### Using App Automation Interface

You can also utilize LambdaTest's user-friendly UI to upload the files on Lambdatest cloud and get the `media_url` using the upload button located at the top of the automation dashboard.

----

### Step 2 : Setting Capability in Your Test Script

Once the files are uploaded to LambdaTest's cloud, seamlessly integrate files into your automation tests via the capability. Set the **uploadMedia** capability to the **media_url** parameter returned in the API response.

<Tabs className="docs__val">
  <TabItem value="Java" label="Java">
    <div className="lambdatest__codeblock">
      <CodeBlock className="language-java">
        {`DesiredCapabilities desiredCapabilities = new DesiredCapabilities();
desiredCapabilities.setCapability("uploadMedia", Arrays.asList("lt://MEDIAfcdb39b9602d474f825d6002416a3969", "lt://MEDIA8d13e569b3e140c18e82b066022518bd"));`}
      </CodeBlock>
    </div>
  </TabItem>

  <TabItem value="JavaScript" label="JavaScript">
    <div className="lambdatest__codeblock">
      <CodeBlock className="language-javascript">
        {`DesiredCapabilities desiredCapabilities = new DesiredCapabilities();
desiredCapabilities.setCapability("uploadMedia", ["lt://MEDIAfcdb39b9602d474f825d6002416a3969", "lt://MEDIA8d13e569b3e140c18e82b066022518bd"]);`}
      </CodeBlock>
    </div>
  </TabItem>
  
  <TabItem value="python" label="Python" default>
    <div className="lambdatest__codeblock">
      <CodeBlock className="language-python">
        {`desired_capabilities = {
  "uploadMedia": ["lt://MEDIAf446d4170cd946aa9ec307d10cb679b9", "lt://MEDIA8d13e569b3e140c18e82b066022518bd"]
}`}
      </CodeBlock>
    </div>
  </TabItem>
</Tabs>

:::note

- Each automation session permits a maximum of five file uploads.
- In manual testing, iOS app needs to installed first to upload non-media files.
- For non-media files, make sure your iOS app's Info.plist file includes the UIFileSharingEnabled and LSSupportsOpeningDocumentsInPlace keys set to true. This configuration is necessary to enable your app's folder accessibility within the Files app.

:::

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
      Camera Image Injection
      </span>
    </li>
  </ul>
</nav>
