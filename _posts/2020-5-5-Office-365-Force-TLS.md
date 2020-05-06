---
layout: post
title: Office 365 - Force TLS
categories: O365
tags:
  - O365
  - Security
---

In order to enforce TLS to secure e-mail connections in Office 365 to and from a particular domain, you can use connectors.

By default, Exchange uses opportunistic TLS. Follow the steps below to set up connectors:

1. Login to <a href="https://admin.microsoft.com/AdminPortal/Home#/homepage">Microsoft 365 admin center</a>, and navigate to the admin center for Exchange.
2. Click on "mail flow" in the left nav.
3. Click on connectors.

### <a href="https://docs.microsoft.com/en-us/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner#set-up-a-connector-to-apply-security-restrictions-to-mail-sent-from-office-365-to-your-partner-organization">Set up the outbound connector</a>

---

![2020-5-5-Send-1](/assets/images/2020-5-5-Send-1.png?raw=true)

---

![2020-5-5-Send-2](/assets/images/2020-5-5-Send-2.png?raw=true)

---

![2020-5-5-Send-3](/assets/images/2020-5-5-Send-3.png?raw=true)

---

![2020-5-5-Send-4](/assets/images/2020-5-5-Send-4.png?raw=true)

---

![2020-5-5-Send-5](/assets/images/2020-5-5-Send-5.png?raw=true)

---

Send a test e-mail to an address at the domain to validate the connector:

![2020-5-5-Send-6](/assets/images/2020-5-5-Send-7.png?raw=true)

---

### <a href="https://docs.microsoft.com/en-us/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner#set-up-a-connector-to-apply-security-restrictions-to-mail-sent-from-your-partner-organization-to-office-365">Set up the inbound connector</a>

---

![2020-5-5-Receive-1](/assets/images/2020-5-5-Receive-1.png?raw=true)

---

![2020-5-5-Receive-2](/assets/images/2020-5-5-Receive-2.png?raw=true)

---

![2020-5-5-Receive-3](/assets/images/2020-5-5-Receive-3.png?raw=true)

---

![2020-5-5-Receive-4](/assets/images/2020-5-5-Receive-4.png?raw=true)

---

![2020-5-5-Receive-5](/assets/images/2020-5-5-Receive-5.png?raw=true)

---

### Review connectors
![2020-5-5-Outcome](/assets/images/2020-5-5-Outcome.png?raw=true)

Jason Sears
