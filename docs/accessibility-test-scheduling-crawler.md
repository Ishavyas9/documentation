---
id: accessibility-test-crawler
title: Accessibility Crawler
sidebar_label: URL Crawler
description: Learn how to use LambdaTest’s Crawler to automate URL extraction for accessibility testing. Configure crawl settings, include/exclude URL patterns, and analyze scan results.
keywords:
    - LambdaTest
    - Accessibility
    - Crawler
    - Testing
    - URL Extraction
url: https://www.lambdatest.com/support/docs/accessibility-test-crawler/
site_name: LambdaTest
slug: accessibility-test-crawler/
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
import NewTag from '../src/component/newTag';

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
          "name": "LambdaTest URL Crawler",
          "item": "https://www.lambdatest.com/support/docs/accessibility-test-crawler/"
        }]
      })
    }}
></script>


## Why LambdaTest Crawler is Helpful for Accessibility Testing

In accessibility testing, ensuring that all relevant URLs across a website are properly tested is crucial. Manual URL entry can be cumbersome and inefficient, especially for large websites with many pages. This is where LambdaTest’s URL Crawler comes into play, offering an automated and streamlined solution for accessibility testing.

With the LambdaTest Crawler, you can:

- **Automatically extract URLs** from your site based on set parameters like crawl depth and maximum pages to be crawled.
- **Scan large websites efficiently** without having to manually input each URL, saving time and resources.
- **Crawl dynamically** generated content and sub-pages that might otherwise be missed in traditional testing methods.
- **Ensure thorough coverage** by including/excluding specific URL patterns, which helps in targeting exactly the content you need to test for accessibility compliance.

By automating the URL discovery process, the LambdaTest Crawler allows you to focus on accessibility issues without missing any pages that might contain potential accessibility barriers.


## Step 1: Access the URL Crawler Feature  
- Open the LambdaTest Accessibility Testing Dashboard.  
- Select the “Crawler” option from the “Add URLs” section.



## Step 2: Configure Crawler Settings  
- **Base URL:** Enter the domain from which you want to start crawling. This is the root URL for the crawler.  
- **Crawl Depth:** Define how deep the crawler should go to fetch additional pages. For example, a depth of 2 will crawl the base URL and its immediate sub-pages.  
- **Max Pages:** Set a limit on the maximum number of pages the crawler should scan. This is useful to prevent unnecessary resource consumption.

<img loading="lazy" src={require('../assets/images/accessibility-testing/schedule-scan/crawler.png').default} className="doc_img"/>

## Step 3: Define URL Patterns (Optional)  
You can fine-tune your URL crawling by including or excluding certain URLs based on patterns.

<Tabs className="docs__val">  

<TabItem value="include" label="Include URL Patterns" default>  
- Enter regular expressions (regex) to include only certain URLs. For example, you can filter by page types, such as `.*\.html` to include only `.html` pages.  
- Multiple patterns can be entered, separated by commas.  

</TabItem>  

<TabItem value="exclude" label="Exclude URL Patterns">  
- Similarly, enter regex patterns to exclude specific URLs. For instance, you can use `.*\.pdf` to exclude PDF files from being crawled.  
- Multiple exclude patterns can be entered, separated by commas.  


</TabItem>  

</Tabs>  



## Step 6: Analyze the Scan Report  
Once the scan is complete, you can analyze the scan report, which includes:  
- **Total Issues:** A graph summarizing the detected accessibility issues.  
- **Severity Trends:** Categorized by severity (Critical, Serious, Moderate, Minor).  
- **Pages Scanned:** View details of each URL crawled, along with a breakdown of issues per URL.

You can drill down into individual URLs for a more detailed analysis of accessibility issues.



> Note: The crawler functionality is available only when creating a new scheduled scan, not for scans that have already been scheduled.



