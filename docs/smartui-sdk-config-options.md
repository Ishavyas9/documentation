---
id: smartui-sdk-config-options
title: SmartUI SDK Advanced Configuration Options
sidebar_label: Configuration Options
description: In this documentation, learn about the options available in SmartUI SDK configuration
keywords:
  - Visual Regression
  - Visual Regression Testing Guide
  - Visual Regression Test Automation
  - Visual Regression Automation Testing
  - Running Visual Regression Tests
  - Visual Regression Testing Online
  - Run Visual Regression
  - Visual Regression Run Specific Test
  - Visual Regression Testing Environment
  - How to Run Visual Regression Tests

url: https://www.lambdatest.com/support/docs/smartui-cli/
slug: smartui-sdk-config-options/
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
import NewTag from '../src/component/newTag';

---

<script type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify({
       "@context": "https://schema.org",
        "@type": "BreadcrumbList",
        "itemListElement": [{
          "@type": "ListItem",
          "position": 1,
          "name": "LambdaTest",
          "item": "https://www.lambdatest.com"
        },{
          "@type": "ListItem",
          "position": 2,
          "name": "Support",
          "item": "https://www.lambdatest.com/support/docs/"
        },{
          "@type": "ListItem",
          "position": 3,
          "name": "Smart Visual Testing",
          "item": "https://www.lambdatest.com/support/docs/smartui-sdk-config-options/"
        }]
      })
    }}
></script>

Welcome to the world of simplified visual testing with the SmartUI SDK.

This guide is designed to provide you with comprehensive information about the various configuration options available within the SmartUI SDK. Whether you're a new user seeking to customize your SmartUI integration or an experienced developer looking to optimize your testing workflows, this documentation will serve as your go-to resource for understanding and utilizing the configuration options effectively. 

To generate the SmartUI SDK configuration file, please execute the following command:

```bash
npx smartui config:create .smartui.json
```

# Configuration File Structure

The SmartUI configuration file follows a JSON structure. Below is a sample configuration file with detailed explanations of each option:

```json
{
  "web": {
    "browsers": [
      "chrome",
      "firefox",
      "safari",
      "edge"
    ],
    "viewports": [
      [1920],
      [1366],
      [1028]
    ]
  },
  "mobile": {
    "devices": [
      "iPhone 14",
      "Galaxy S24"
    ],
    "fullPage": true,
    "orientation": "portrait"
  },
  "waitForTimeout": 1000,
  "waitForPageRender": 50000,
  "enableJavaScript": false,
  "allowedHostnames": ["cdn.xyz.com"]
}
```
## 1. Web Configuration

### 1.1 browsers: 
An array of browsers to capture screenshots from. Supported browsers include `chrome`, `firefox`, `safari`, and `edge`.

### 1.2 viewports: 
An array of arrays representing different screen resolutions for web browsers. Each inner array contains viewport sizes. 
Each web viewport is automatically rendered for each of the browser mentioned in the config.

#### 1.2.1 For capturing fullpage screenshots

To capture a screenshot of the entire page, you only need to define the viewport width in your configuration settings. Specify the desired width parameters as demonstrated in the following example to ensure a fullpage capture.

```json title="Full Page Capture"
    "viewports": [
      [
        1920
      ],
      [
        1366
      ],
      [
        360
      ]
    ],
```

#### 1.2.2 For capturing viewport screenshots

To capture a screenshot of the content currently visible in your viewport, rather than the entire page, it's important to define the viewport's width and height in your configuration settings. Specify the desired width and height parameters as demonstrated in the following example to ensure that the screenshot encompasses only the viewport area.

```json title="Viewport Capture"
    "viewports": [
      [
        1920,
        1080
      ],
      [
        1366,
        768
      ],
      [
        360,
        640
      ]
    ],
```

## 2. Mobile Configuration

### 2.1 devices: 
An array of mobile devices to capture screenshots from. List of supported device names can be found [here](#list-of-supported-device-viewports). 

:::note
 Mobile viewports are emulated in desktop environments.Android devices will have the screenshots rendered in Chrome, while iOS devices in Safari.
 SmartUI SDK will soon be supported simulation in case of iOS devices.
:::

### 2.2 fullPage: 
Specifies whether to capture full-page screenshots for mobile devices. <b>By default</b>, `fullPage` is taken as <b>true</b>; set it to `false` in order to take a viewport screenshot on a mobile viewport.

### 2.3 orientation: 
Specifies the orientation of the mobile device. You can choose from `portrait` or `landscape` according to your usecase. <b>By default</b>, the orientation is taken as <b>portrait</b>.

## 3. Global Options (Optional)

### 3.1 waitForPageRender:
If one or more URLs in your script require a relatively higher amount of time to load, you may use the `waitForPageRender` key in the config file to make sure the screenshots are rendered correctly. Avoid using the same in case your websites render in less than 30 seconds as it might increase the execution time of your tests.

### 3.2 waitForTimeout: 
If you are using any async components, you can add wait time for the page to load the DOM of your components. This can help avoid false-positive results for your tests. You can add the wait time in milliseconds, which might increase the execution time of your tests.

### 3.3 enableJavaScript:
The `enableJavaScript` option is a boolean parameter that determines whether JavaScript is enabled for all snapshots within the project. Enabling JavaScript may lead to side-effects such as animations or redirects, potentially affecting the reliability of your snapshots.  <b>By default</b>, this option is set to <b>false.</b>

### 3.4 allowedHostnames: 
The `allowedHostnames` option controls the capture of assets from specific hostnames. By default, the SmartUI SDK only captures assets that match the hostname of the snapshot location. For instance, if snapshots are taken on `https://xyz.com`, assets hosted on `https://cdn.xyz.com` will not be captured. To include assets from other hostnames, each additional hostname needs to be added to the allowedHostnames configuration.


For additional information about SmartUI APIs please explore the documentation [here](https://www.lambdatest.com/support/api-doc/)

## List of supported Device viewports

| IOS Devices            | Android Devices             |
|------------------|------------------------|
| iPad 10.2 (2019)| Blackberry KEY2 LE     |
| iPad 10.2 (2020)| Galaxy A12             |
| iPad 10.2 (2021)| Galaxy A21s            |
| iPad 9.7 (2017) | Galaxy A22             |
| iPad Air (2019) | Galaxy A31             |
| iPad Air (2020) | Galaxy A32             |
| iPad Air (2022) | Galaxy A51             |
| iPad mini (2019)| Galaxy A7              |
| iPad mini (2021)| Galaxy A70             |
| iPad Pro 11 (2021)| Galaxy A70           |
| iPad Pro 11 (2022)| Galaxy A8            |
| iPad Pro 12.9 (2018)| Galaxy A8+         |
| iPad Pro 12.9 (2020)| Galaxy J7 Prime    |
| iPad Pro 12.9 (2021)| Galaxy M12         |
| iPad Pro 12.9 (2021)| Galaxy M31         |
| iPad Pro 12.9 (2022)| Galaxy Note10      |
| iPhone 11        | Galaxy Note10+         |
| iPhone 11        | Galaxy Note20          |
| iPhone 11 Pro    | Galaxy Note20 Ultra 5G |
| iPhone 11 Pro Max| Galaxy S10             |
| iPhone 12        | Galaxy S10+            |
| iPhone 12        | Galaxy S10e            |
| iPhone 12 Mini   | Galaxy S20             |
| iPhone 12 Pro    | Galaxy S20 FE          |
| iPhone 12 Pro Max| Galaxy S20 Ultra       |
| iPhone 13        | Galaxy S20+            |
| iPhone 13 Mini   | Galaxy S21 5G          |
| iPhone 13 Pro    | Galaxy S21 FE          |
| iPhone 13 Pro Max| Galaxy S21 Ultra 5G    |
| iPhone 14        | Galaxy S21+            |
| iPhone 14 Plus   | Galaxy S21+ 5G         |
| iPhone 14 Pro    | Galaxy S22 5G          |
| iPhone 14 Pro Max| Galaxy S22 Ultra 5G    |
| iPhone 15        | Galaxy S23             |
| iPhone 15 Plus   | Galaxy S23 Ultra       |
| iPhone 15 Pro    | Galaxy S23+            |
| iPhone 15 Pro Max| Galaxy S24             |
| iPhone 6         | Galaxy S24+            |
| iPhone 6s        | Galaxy S24 Ultra       |
| iPhone 6S Plus   | Galaxy S7              |
| iPhone 7         | Galaxy S7 Edge         |
| iPhone 7 Plus    | Galaxy S8              |
| iPhone 8         | Galaxy S8+             |
| iPhone 8         | Galaxy S9              |
| iPhone 8 Plus    | Galaxy S9+             |
| iPhone SE (2016)| Galaxy Tab A7 Lite     |
| iPhone SE (2020)| Galaxy Tab A8          |
| iPhone SE (2022)| Galaxy Tab S3          |
| iPhone X         | Galaxy Tab S4          |
| iPhone XR        | Galaxy Tab S7          |
| iPhone XS        | Galaxy Tab S8          |
| iPhone XS Max    | Galaxy Tab S8+         |
|                  | Huawei Mate 20 Pro     |
|                  | Huawei P20 Pro         |
|                  | Huawei P30             |
|                  | Huawei P30 Pro         |
|                  | Microsoft Surface Duo  |
|                  | Moto G7 Play           |
|                  | Moto G9 Play           |
|                  | Moto G Stylus 5G (2022)|
|                  | Nexus 5                |
|                  | Nexus 5X               |
|                  | Nokia 5                |
|                  | Nothing Phone (1)      |
|                  | OnePlus 10 Pro         |
|                  | OnePlus 11             |
|                  | OnePlus 6              |
|                  | OnePlus 6T             |
|                  | OnePlus 7              |
|                  | OnePlus 7T             |
|                  | OnePlus 8              |
|                  | OnePlus 9              |
|                  | OnePlus 9 Pro          |
|                  | OnePlus Nord           |
|                  | OnePlus Nord 2         |
|                  | OnePlus Nord CE        |
|                  | Oppo A12               |
|                  | Oppo A15               |
|                  | Oppo A54               |
|                  | Oppo A5s               |
|                  | Oppo F17               |
|                  | Oppo K10               |
|                  | Pixel 3                |
|                  | Pixel 3 XL             |
|                  | Pixel 3a               |
|                  | Pixel 4                |
|                  | Pixel 4 XL             |
|                  | Pixel 4a               |
|                  | Pixel 5                |
|                  | Pixel 6                |
|                  | Pixel 6 Pro            |
|                  | Pixel 7                |
|                  | Pixel 7 Pro            |
|                  | Pixel 8                |
|                  | Pixel 8 Pro            |
|                  | Poco M2 Pro            |
|                  | POCO X3 Pro            |
|                  | Realme 5i              |
|                  | Realme 7i              |
|                  | Realme 8i              |
|                  | Realme C21Y            |
|                  | Realme C21             |
|                  | Realme GT2 Pro         |
|                  | Redmi 8                |
|                  | Redmi 9                |
|                  | Redmi 9A               |
|                  | Redmi 9C               |
|                  | Redmi Note 10 Pro      |
|                  | Redmi Note 8           |
|                  | Redmi Note 8 Pro       |
|                  | Redmi Note 9           |
|                  | Redmi Note 9           |
|                  | Redmi Note 9 Pro Max   |
|                  | Redmi Y2               |
|                  | Tecno Spark 7          |
|                  | Vivo Y22               |
|                  | Vivo T1 5G             |
|                  | Vivo V7                |
|                  | Vivo Y11               |
|                  | Vivo Y12               |
|                  | Vivo Y20g              |
|                  | Vivo Y50               |
|                  | Xiaomi 12 Pro          |
|                  | Xperia Z5              |
|                  | Xperia Z5 Dual         |
|                  | Zenfone 6              |




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
      <span className="breadcrumbs__link"> Smart UI with Cypress  </span>
    </li>
  </ul>
</nav>
