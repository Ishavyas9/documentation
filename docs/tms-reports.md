---
id: tms-reports
title: Reports
hide_title: true
sidebar_label: Reports
description: View & Download the Execution & Traceability reports for Test Instances execution.
keywords:
  - reports
  - execution 
  - traciability
url: https://www.lambdatest.com/support/docs/tms-reports/
site_name: LambdaTest
slug: tms-reports/
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
          "name": "Reports",
          "item": "https://www.lambdatest.com/support/docs/tms-reports/"
        }]
      })
    }}
></script>

# Reports in Test Manager  

Test Manager provides powerful reporting capabilities to help teams gain actionable insights from their testing activities. With **Execution and Traceability Reports**, you can measure test coverage, track progress, and ensure alignment between requirements, test cases, and defects.  

To access the reports you need to go inside the `Reports` section present inside a Project. 

<img loading="lazy" src={require('../assets/images/mobile-app-testing/Reports/Reports-listing-page.png').default} alt="Reports Overview" className="doc_img"/>

There are two type of Reports that you can create here:

<img loading="lazy" src={require('../assets/images/mobile-app-testing/Reports/select-report-type.png').default} alt="Reports Overview" className="doc_img"/>

---

## Execution Reports  

Execution based reports allow you to analyze the results of your test executions and identify patterns in test execution.  

When you create an Execution Report, you have two ways to filter the data:

### 1. Filter By Test Runs: 
This option lets you include the results from specific test runs you select.

<img loading="lazy" src={require('../assets/images/mobile-app-testing/Reports/runs-based-execution-report.png').default} alt="Reports Overview" className="doc_img"
  style={{ width: '60%', height: 'auto'}}/>

### 2. Filter By Date: 
This option allows you to see all test results that were generated within a specific date range.

<img loading="lazy" src={require('../assets/images/mobile-app-testing/Reports/date-based-execution-report.png').default} alt="Reports Overview" className="doc_img"
  style={{ width: '60%', height: 'auto'}}/>

You can optionally add **Description** for the Report too but adding **Name** is mandatory to proceed here. 

**Recurring Reports:**
You can select the `Recurring` option, add **Reciepients** & **Frequency** to automatically get the mail notification with the reports timely. 

This is how the execution reports will look like:

<img loading="lazy" src={require('../assets/images/mobile-app-testing/Reports/execution-report.png').default} alt="Reports Overview" className="doc_img"/>

:::tip
 All the Reports can be Downloaded as CSV files.  
:::

---

## Traceability Reports  

Traceability reports provide end-to-end visibility into how your test cases align with business requirements and defects.  

The Traceability reports show the Issues based test-execution report allowing you ti see the Issues coverage in tests:

<img loading="lazy" src={require('../assets/images/mobile-app-testing/Reports/traciability-report.png').default} alt="Reports Overview" className="doc_img"/>

You can filter the Report data with Test, Issues & Runs meta data. using the filters:

<img loading="lazy" src={require('../assets/images/mobile-app-testing/Reports/traciablity-filters.png').default} alt="Reports Overview" className="doc_img"/>

---
