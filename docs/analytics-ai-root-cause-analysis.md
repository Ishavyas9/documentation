---
id: analytics-ai-root-cause-analysis
title: AI Root Cause Analysis (AI RCA) - Test Intelligence
sidebar_label: AI Root Cause Analysis
description: Automatically analyze test failures with AI-powered Root Cause Analysis. Get instant insights into test failure patterns and accelerate debugging with actionable RCA results.
keywords:
  - analytics
  - AI RCA
  - root cause analysis
  - test intelligence
  - test failure analysis
  - debugging
  - AI insights
url: https://www.lambdatest.com/support/docs/analytics-ai-root-cause-analysis/
site_name: LambdaTest
slug: analytics-ai-root-cause-analysis/
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
          "name": "AI Root Cause Analysis",
          "item": "https://www.lambdatest.com/support/docs/analytics-ai-root-cause-analysis/"
        }]
      })
    }}
></script>

AI Root Cause Analysis (AI RCA) in LambdaTest Analytics automatically analyzes failed tests to identify probable root causes and provides actionable insights to improve test stability and reduce debugging time. This AI-powered feature accelerates your debugging process by eliminating manual investigation and providing instant, comprehensive failure analysis.

## What is AI Root Cause Analysis?

AI RCA is an intelligent feature that uses advanced machine learning algorithms to automatically analyze test failures and identify their root causes. Instead of manually sifting through logs and error messages, AI RCA provides:

- **Automated failure analysis** that runs immediately when tests fail
- **Intelligent root cause identification** distinguishing between primary causes and cascading symptoms
- **Actionable steps to fix** with specific fixes and recommendations
- **Historical trend analysis** to identify recurring issues and patterns
- **Comprehensive error timelines** showing the sequence of events leading to failures

## Prerequisites for AI RCA

1. **Active LambdaTest Account**: You should have an active LambdaTest account with appropriate permissions.
2. **Subscription Plan**: This feature is available for users with HyperExecute or App/Web Automation subscription plans.
3. **Available Credits**: Tests will only be processed through RCA when sufficient credits are available. For more information on credit management, see our [Credits Management](/docs/credits-management/) documentation.
4. **Test Failures**: AI RCA requires at least one test failure to generate analysis. The system learns from your test execution patterns.
5. **Access to Insights**: You should have access to the LambdaTest Insights platform under **Insights** tab.

## Configuration & Setup

<img loading="lazy" src={require('../assets/images/analytics/test-intelligence-ai-test-rca-configuration.png').default} alt="cmd" width="800" height="400" className="doc_img"/>

### Step 1: Access Organization Settings

1. Navigate to **Organization Settings** in your LambdaTest dashboard
2. In the left sidebar, expand the **Insights** section under **Org Product Preferences**
3. Select **Automatic AI RCA** from the available options

### Step 2: Enable AI RCA

1. **Toggle the Feature**: Use the blue toggle switch to enable "Automatic AI RCA"
2. **Configure Analysis Scope**: Choose which types of test failures to analyze:
   - **All failures**: Analyze every failed test, regardless of previous status
   - **New failures**: Analyze only tests that have failed recently after having passed at least 10 consecutive times previously.
   - **Always failing**: Analyze only tests that have failed in all of their previous 5 runs to identify persistent issues.

### Step 3: Set Special Instructions (Optional)

Provide context or specific guidance for the AI to consider during analysis:

1. Click on the **Special Instructions** section
2. Enter any special instructions or context that should be considered during AI root cause analysis
3. Use the "Show examples" link for guidance on effective instruction writing

**Example Instructions:**

:::tip
Our CRM application has specific failure patterns to watch for:

**PRIORITY CATEGORIES**
1. **Database Connection Issues** - Our PostgreSQL connection pool is limited to 20 connections. Look for connection timeouts, pool exhaustion, or slow query performance.

2. **Third-party API Failures** - We integrate with Salesforce, HubSpot, and Mailchimp. These external APIs often have rate limits and intermittent failures that cause our tests to fail.

3. **File Upload/Processing Issues** - Contact import via CSV files often fails due to file size limits (10MB max) or malformed data. Check for upload timeouts and validation errors.

4. **Authentication/Authorization** - We use OAuth 2.0 with multiple providers. Token expiration and permission changes frequently cause test failures.

5. **UI Element Timing Issues** - Our CRM uses dynamic loading for contact lists and reports. Elements may not be ready when tests try to interact with them.

**SPECIFIC CONTEXT**
- Our test environment has limited resources compared to production
- We run tests during business hours when external APIs are under heavy load
- Focus on identifying whether failures are environment-specific or application bugs
- Prioritize failures that affect core CRM functionality (contact management, lead tracking, reporting)
- Consider our custom error handling - we log all errors to Sentry and show user-friendly messages

**IGNORE THESE COMMON FALSE POSITIVES**
- Browser console warnings that don't affect functionality
- Network requests to analytics services (Google Analytics, Hotjar)
- Minor UI layout shifts that don't break functionality
:::

**Possible Categories and Descriptions:**

| Category | Description | When to Use |
|----------|-------------|-------------|
| **Database Issues** | Connection timeouts, query performance, data integrity problems | When tests fail during data operations (CRUD, reports, imports) |
| **API Integration** | Third-party service failures, rate limiting, authentication issues | When tests interact with external services (Salesforce, payment gateways) |
| **UI/UX Problems** | Element not found, timing issues, responsive design failures | When tests fail on user interface interactions |
| **Performance Issues** | Slow page loads, memory leaks, resource exhaustion | When tests timeout or run very slowly |
| **Environment Issues** | Test data problems, configuration mismatches, infrastructure failures | When failures are environment-specific rather than code issues |
| **Authentication/Authorization** | Login failures, permission errors, session timeouts | When tests fail during user authentication or access control |
| **File Processing** | Upload failures, format validation, processing timeouts | When tests involve file operations (imports, exports, attachments) |
| **Network Issues** | Connectivity problems, DNS failures, proxy issues | When tests fail due to network-related problems |

### Step 4: Configure Intelligent Targeting

Configure intelligent targeting rules to precisely control which tests, builds, tags, or jobs are included in AI-powered analysis:

1. **Add Targeting Rules**: Enter regex patterns in the input field
2. **Click Include (+) or Exclude (-)**: Choose whether to include or exclude matching tests
3. **Configure Multiple Criteria**: Set targeting rules for:
   - **Test Names**: Target specific test suites or test patterns
   - **Build Tags**: Include or exclude builds with specific tags
   - **Test Tags**: Include or exclude tests with specific tags (e.g., playwright_test, atxHyperexecute_test)
   - **Build Tags**: Include or exclude builds with specific tags (e.g., hourly, nightly)
   - **Job Labels**: Include tests with specific job labels or tags

#### Example Configuration

:::tip
**Test Name:**
- **Include**: `.*prod.*` - Only analyze tests with name containing "prod"
- **Exclude**: `.*non-critical.*` - Skip tests with name containing "non-critical"

**Build Tag:**
- **Include**: `^hourly` - Only analyze builds with tag starting with "hourly"

**Failure Type:**
- **Include**: `ApiError5xx|ResourceLoadFailure` - Focus on API and resource loading failures
- **Exclude**: `TestScriptError` - Skip script-related errors for this analysis

**Browser/OS:**
- **Include**: `Chrome.*MacOS|Chrome.*Windows` - Target Chrome on Mac and Windows
- **Exclude**: `.*Linux.*` - Skip Linux environments

**Test Tags:**
- **Include**: `playwright_test|atxHyperexecute_test` - Focus on specific test frameworks
- **Exclude**: `.*smoke.*` - Skip smoke tests

**Result**: AI-powered analysis will run only on production tests (excluding non-critical ones) from hourly builds, focusing on API and resource failures in Chrome browsers on Mac/Windows, using Playwright or HyperExecute test frameworks, while excluding smoke tests.
:::


### Step 5: Save Configuration

1. Click **Save Configuration** to apply your settings
2. The settings will be applied to all users in your organization and cannot be modified by individual users or need admin level privileges.

## RCA Output & Interpretation

### Where to View RCA Results

AI RCA results are available in multiple locations across the LambdaTest platform:

1. **TMS Dashboard**: View RCA results directly in your test execution dashboard
2. **HyperExecute Dashboard**: Access detailed RCA analysis for HyperExecute jobs
3. **Insights Dashboard**: Comprehensive RCA analytics and trend analysis

<img loading="lazy" src={require('../assets/images/analytics/test-intelligence-ai-test-rca-insights.png').default} alt="cmd" width="800" height="400" className="doc_img"/>

### Understanding RCA Output

The RCA output provides a unified analysis with:

- **Primary Root Cause**: The main issue identified by AI analysis
- **Cascading Symptoms**: Secondary issues that contribute to the problem but aren't the primary cause
- **Severity Level**: High, Medium, or Low severity classification
- **Error Category**: JavaScript Error, Network Error, Environment Issue, etc.

<details>
<summary>View Example RCA</summary>

**Example RCA Summary:**
> **Problem**: Contact creation test fails after 30 seconds  
> **Root Cause**: Database connection pool is full (10/10 connections used)  
> **Impact**: New contact requests wait in queue until connections free up  
> **Fix**: Increase connection pool from 10 to 50 connections

#### Error Timeline

The Error Timeline provides a chronological sequence of events leading to the failure:

**Example Timeline for CRM Contact Creation Test Failure:**
1. **Test starts** - Navigate to contacts page (1s)
2. **Fill form** - Enter contact details (3s)  
3. **Click submit** - Create contact button clicked (4s)
4. **Connection issue** - Database pool full, request queued (4s)
5. **Wait timeout** - No connections available (30s)
6. **Test fails** - "Contact creation timeout"

#### Steps to Fix

Each RCA includes specific, actionable steps to fix with clear implementation guidance:

**Database Connection Issues:**
- **Quick Fix**: Increase connection pool from 10 to 50
- **Code**: `spring.datasource.hikari.maximum-pool-size=50`
- **Test Fix**: Add connection health check before form submission

**Form Submission Failures:**
- **Quick Fix**: Add retry logic with 3 attempts
- **Code**: `retry(createContact, { maxAttempts: 3, delay: 2000 })`
- **Test Fix**: Mock database calls in test environment

**Performance Issues:**
- **Quick Fix**: Increase timeout to 45 seconds
- **Code**: `waitForElement('#success-message', { timeout: 45000 })`
- **Test Fix**: Use lightweight test data

</details>

### RCA Category Trends Widget

The RCA Category Trends widget in Insights enables you to:

1. **View Historical Trends**: See how different RCA categories have evolved over time
2. **Drill Down Analysis**: Click on specific categories to analyze test failure patterns
3. **Identify Recurring Issues**: Spot patterns in failure types to prioritize fixes
4. **Track Improvement**: Monitor the effectiveness of your remediation efforts

<img loading="lazy" src={require('../assets/images/analytics/test-intelligence-ai-test-rca-widget.png').default} alt="cmd" width="800" height="400" className="doc_img"/>

## Best Practices

### 1. Effective Configuration

- **Start with "All failures"** to get comprehensive coverage, then refine based on your needs
- **Use specific special instructions** to guide the AI toward your most critical issues
- **Set up intelligent targeting** to focus on relevant test suites and exclude noise

### 2. Interpreting Results

- **Focus on primary root causes** rather than cascading symptoms
- **Prioritize high-severity issues** for immediate attention
- **Use the error timeline** to understand the sequence of events
- **Apply steps to fix systematically** starting with the most critical fixes

### 3. Continuous Improvement

- **Review RCA accuracy** and provide feedback when possible
- **Monitor trend analysis** to identify recurring patterns
- **Update special instructions** based on new insights and requirements
- **Share RCA results** with your team to improve collective understanding

<!-- ### 4. Integration with Workflow

- **Set up alerts** for high-severity RCA findings
- **Create tickets** directly from RCA results for systematic tracking
- **Use RCA data** in sprint planning to prioritize bug fixes
- **Document successful fixes** to build institutional knowledge -->

## Troubleshooting Common Issues

<details>
<summary><strong>RCA Not Generating</strong></summary>

- **Check prerequisites**: Ensure you have the required subscription plan
- **Verify credits availability**: AI RCA processing requires credits to be available in your account. Check your [Credits Management](/docs/credits-management/) page to ensure sufficient credits
- **Verify test failures**: AI RCA requires actual test failures to analyze
- **Review configuration**: Confirm AI RCA is enabled in organization settings
- **Check permissions**: Ensure you have access to Analytics and Test Intelligence features

</details>

<details>
<summary><strong>Inaccurate RCA Results</strong></summary>

- **Refine special instructions**: Provide more specific context about your application
- **Update intelligent targeting**: Exclude irrelevant tests that might confuse the analysis
- **Review error categorization**: Ensure test failures are properly categorized
- **Provide feedback**: Use any available feedback mechanisms to improve accuracy

</details>

<details>
<summary><strong>Missing RCA Data</strong></summary>

- **Check time range**: Ensure you're looking at the correct time period
- **Verify test execution**: Confirm tests actually failed during the specified period
- **Review dashboard filters**: Check if any filters are excluding relevant data
- **Contact support**: Reach out if RCA data appears to be missing

</details>

## Support

For any queries or issues related to AI Root Cause Analysis, please reach out to our [24/7 customer support](mailto:support@lambdatest.com). We're here to help you maximize the value of this powerful debugging tool!

---

**Related Documentation:**
- [Smart Tags - Test Intelligence](/docs/analytics-smart-tags-test-intelligence/)
- [Failure Categorization AI](/docs/analytics-test-failure-classification/)
- [Test Insights Overview](/docs/analytics-test-insights/)
