---
layout: twoColumn
section: Business verified customer
type: article
title:  Frequently Asked Questions
weight: 4
description: Frequently asked questions for business verified Customers
---
# Frequently Asked Questions

## Customer Eligibility

##### Q: My Customer has a `retry` status. What activity would they able to engage in while being in ‘retry’ status, as it relates to the Dwolla Platform?

+ Send funds - No
+ Receive funds - Yes - Note that funds will only process to their balance and the transfer will stay `pending` until the Customer has been verified.
+ Add and verify a bank funding source - Yes
+ Add and verify a Beneficial Owner - Yes

##### Q: My Customer has a `document` status. What activity would they able to engage in while being in ‘document’ status, as it relates to the Dwolla Platform?

+ Send funds - No
+ Receive funds - Yes - Note that funds will only process to their balance and the transfer will stay `pending` until the Customer has been verified.
+ Add and verify a bank funding source - Yes
+ Add and verify a Beneficial Owner - Yes

##### Q: My Customer has a `deactivated` or `suspended` status. What activity would they able to engage in while being in ‘deactivated’ or ‘suspended’ status, as it relates to the Dwolla Platform?

+ Send funds - No
+ Receive funds - No
+ Add and verify a bank funding source - No
+ Add and verify a Beneficial Owner -  No

##### Q: My Customer has a `verified` status, but unable to send funds. Why is this?

+ Your Customer has likely not completed the bank verification process. You can check to see the status of the funding source [via the API](https://docs.dwolla.com/#list-funding-sources-for-a-customer) or  by going into the [Dwolla dashboard](https://www.dwolla.com/platform/dashboard/).

##### Q: Can I `change` a ‘business verified’ Customer type to an `Unverified` Customer type?

+ No. Downgrade functionality is not supported for Dwolla Verified Customers.

##### Q: My Customer has a `document` status. Can I submit more than one document via the API?

+ Yes, although this is not necessary, nor recommended. Dwolla manually reviews all documents, so sending more documents than necessary may slow down the verification process for your Customers.

##### Q: My end user is not a US resident, can they still create a Personal Verified Customer via the API to access my application?

+ No. At this time, Dwolla will create Business Verified Customers when they have a proper business EIN or SSN (for Sole Proprietorships only).

##### Q: My Customer needs to send more funds than is allowed in my Dwolla services agreement. What is the best way to go about this?

+ Your Customer is able to send multiple separate transfers as long as each transfer amount is less than the transfer limit defined in your services agreement.

      > Example Scenario: The transaction limit for my Customer is $10,000 and they need to send $15,000.  
      In this case, you can prompt your Customer to send two transfers. One for $10,000 and another for $5,000.

## Beneficial Owner Eligibility

##### Q: My Business Verified Customer is `verified` and my Beneficial Owners are `verified` but they cannot send funds. Why is this?

+ Your Customer will need to `certify` beneficial ownership information before your Customer will be eligible to send funds.

##### Q: One of my Business Verified Customer’s Beneficial Owners is not yet in a `verified` status. What is my Customer’s eligibility for certain actions with Dwolla?

+ Send funds - No
+ Receive funds - Yes
+ Add and verify a bank funding source - Yes

##### Q: When should my Beneficial Owner use `ssn`? When should they use the `passport`?

+ If your Beneficial Owner is an individual from the United States with a US-issued SSN, your Beneficial Owner will sign up with this method.
+ If your Beneficial Owner is a non-US individual, they will use the `passport` object.

* * *

#### Review previous steps:

* [Creating business verified Customer](/resources/business-verified-customer/create-business-verified-customers.html)
* [Handling business verified Customer statuses](/resources/business-verified-customer/handling-controller-and-customer-statuses.html)
* [Adding beneficial owner(s)](/resources/business-verified-customer/adding-beneficial-owners.html)
* [Certifying beneficial owner(s)](/resources/business-verified-customer/handling-beneficial-owner-certification.html)
