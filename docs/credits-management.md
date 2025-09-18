---
id: credits-management
title: Credits: Usage & Management in LambdaTest
hide_title: true
sidebar_label: Credits Management
description: Guide for usage of credits for AI features in LambdaTest
keywords:
  - credits
  - AI
url: https://www.lambdatest.com/support/docs/credits-management/
site_name: LambdaTest
slug: credits-management/
---

import CodeBlock from '@theme/CodeBlock';
import {YOUR_LAMBDATEST_USERNAME, YOUR_LAMBDATEST_ACCESS_KEY} from "@site/src/component/keys";

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
          "name": "Network Throttling",
          "item": "https://www.lambdatest.com/support/docs/credits-management/"
        }]
      })
    }}
></script>

LambdaTest supports a **credit management system** as an add‑on over your active subscriptions for LambdaTest products. Many products include additional **AI features** that are powered by credits. This guide explains how credits work, how to view usage, and how admins can control consumption.

---

## Who gets credits?

* **Free users:** Receive **1,000 complimentary credits** to try AI‑powered features.
* **Paid users:** Receive **complimentary credits** based on subscription to try AI‑powered features and can purchase credits as an add‑on at any time. Credits are used only when AI features are invoked.

:::tip
Once free credits are exhausted, AI features will be unavailable until you **upgrade or purchase credits** from the Billing page. Use this link to buy credits directly: [Upgrade / Buy Credits](https://billing.lambdatest.com/billing/subscriptions?addCredits=true).

---

## View your current credit balance

If you are an **admin** in LambdaTest organization, you can see the current credits and subscription details in [Billing & Subscriptions](https://billing.lambdatest.com/billing/subscriptions).

---

## View credit transactions

**Admins** can view detailed **debits and credits** for your organization - **[Transactions view](https://billing.lambdatest.com/billing/subscriptions?viewCredits=true)**.

The transactions table shows:

* **Date** of the event
* **Type** (Debit / Credit)
* **Credits** (Amount of credits)
* **Name** of the user who did the transaction

---

## Set credit usage limits (Admins Only)

Admins can define **org‑wide controls** to prevent unexpected consumption:

* **Soft Limit**
  When the soft limit is reached, users are **notified via email**, but usage **continues**.

* **Hard Limit**
  When the hard limit is reached, **no further credit consumption** is allowed. Users are notified via email. To resume, increase the limit or purchase more credits.

:::tip
**Recommendation:** Start with a soft limit (e.g., 70–80% of your monthly plan) and a hard limit (e.g., 90%).

---

## AI features that consume credits

Below are the currently supported features and how they consume credits.

### SmartUI Visual AI

LambdaTest **SmartUI Visual AI** simulates human perception for visual regression. Rather than flagging every pixel change, it highlights **meaningful, human‑relevant** differences between baseline and new screenshots.[Learn more](https://www.lambdatest.com/support/docs/smartui-visual-ai/)

#### How credits are consumed?

**Small / Normal Screenshot**

* A page or screen that fits within a typical device viewport (e.g., one laptop or mobile screen)
* Examples: login page, product details, simple dashboard
* **Consumes \~1–4 credits** (most common)

**Large Screenshot**

* A long or content‑heavy page beyond the standard viewport (full‑page scroll, data‑heavy dashboards)
* Examples: full home page, long reports, multi‑section dashboards
* **Consumes \~5–8 credits** (less common)

:::note
**In summary:** The bigger and more content‑heavy the screenshot, the more credits it consumes.

---

### AI Test Case Generator

The **AI Test Case Generator** converts diverse inputs (text, PDFs, audio, videos, images, Jira tickets, and more) into **structured, contextual test cases**, accelerating authoring while improving coverage. [Learn more](https://www.lambdatest.com/support/docs/generate-test-cases-with-ai/).

#### How credits are consumed

* **10 credits per scenario** generated.
* When you start generation, credits are tentatively consumed based on **Max Scenarios** you select (default **5**).
  Example: Default 5 → **50 credits** tentatively consumed when you begin.
* If fewer scenarios are produced (e.g., **4**), **10 credits are credited back**, so you only pay for what’s actually generated.
* **Regeneration** also consumes credits at **10 credits per scenario**.

:::note
This ensures fair usage—you are charged only for **actual output** produced by the AI.

---

## FAQs

**Q: What happens when my credits run out?**
AI features that require credits will be disabled. You can **purchase credits** or **upgrade** [here](https://billing.lambdatest.com/billing/subscriptions?addCredits=true).

**Q: Who can view balances and transactions?**
Users with the **Admin** role in your LambdaTest organization.

**Q: Do unused credits expire?**
For free users, complimentary credits are provided for one-time usage and do not expire. While for users subscribed to LambdaTest products, the complimentary credits get reset at the beginning of each month. Any credits explicitly purchased, do not expire.

**Q: Why were credits refunded after generation?**
When fewer scenarios than the selected Max Scenarios are generated, the difference is **credited back automatically**.

**Q: Can I cap my organization’s usage?**
Yes—set **Soft** and **Hard** limits (Admins only).

---

## What’s next

Additional AI features will join the credit system shortly. Watch the **LambdaTest Changelog** and Support Docs for updates.

If you have questions about credits, billing, or limits, reach out to **[support@lambdatest.com](mailto:support@lambdatest.com)**.
