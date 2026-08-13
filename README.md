# Order Value & Payment Reconciliation



## Overview

This project explores what happens when finance and operations use the same underlying data but arrive at different answers to what appears to be the same question.

Using the Brazilian E-Commerce Public Dataset by Olist, the analysis compares:

* recorded payment value,
* product value,
* freight value,
* total product plus freight value,
* and order status.

The starting point was simple:

> Does recorded payment value reconcile to product value plus freight?

At headline level, the difference appeared relatively small.

However, once the analysis moved to order level, 1,158 orders required reconciliation review.

The project therefore developed from a straightforward value comparison into a practical finance-and-operations reconciliation case study.

The analysis demonstrates how reporting can move beyond a headline total and identify:

* where differences sit,
* which exceptions require different types of review,
* where additional context is needed,
* and where data completeness affects decision-making.

The project is designed as a practical Power BI decision-support case study suitable for:

* SME finance and operational reporting,
* payment and order-value reconciliation,
* ERP / SAP-style reporting demonstrations,
* Power BI portfolio work,
* data-quality discussions,
* and finance/operations alignment.

---

# The Problem

Finance and operations can use the same data and still arrive at different answers.

That does not necessarily mean one report is wrong.

One team may be looking at product value.

Another may include freight.

Another may use recorded payment value.

Another may exclude orders that have not completed operationally.

The problem starts when all of those figures are described using the same language.

In this dataset, the headline analysis identified:

* 16.01M recorded payment value
* 15.84M product plus freight value
* 0.17M net reconciliation difference
* 13.59M product value
* 2.25M freight value
* 0.10M cancelled / unavailable order value
* 1,158 orders requiring reconciliation review

The headline totals were relatively close.

But positive and negative order-level differences partly cancelled each other when viewed only as a total.

This created a more useful business question:

> If the headline values are close, what is happening underneath them?

The analysis therefore moved away from simply asking whether two totals matched.

Instead, it asked:

* which orders contained a reconciliation difference?
* whether recorded payment value was above or below product plus freight value;
* whether affected orders had already been delivered;
* whether payment instalment information provided useful context;
* and whether missing information created additional review requirements.

This reflects a common reporting challenge:

> A small difference at total level does not mean the underlying records are fully reconciled.

---

# The Approach

The project used the Brazilian E-Commerce Public Dataset by Olist.

Relevant tables included:

* orders,
* order items,
* payments,
* products,
* customers,
* and supporting order-status fields.

The analysis was built in Power BI using Power Query, relational modelling and DAX measures.

The work developed in stages.

## Stage 1: Establish the Headline Position

The first stage compared the main value measures.

Product value was taken from the order-items table.

Freight value was added to create a broader order-value measure.

Recorded payment value was taken from the payments table.

The comparison showed:

* 16.01M recorded payment value
* 15.84M product plus freight value
* 0.17M net difference

At this level, the figures appeared reasonably close.

But that did not establish whether the orders themselves reconciled.

## Stage 2: Move to Order-Level Exceptions

The second stage identified individual orders where recorded payment value differed from product plus freight value.

This produced:

* 1,158 orders requiring reconciliation review.

The exception population was then separated into different groups rather than treated as one generic mismatch.

The first distinction was between:

* orders where payment value was above product plus freight value;
* and orders where payment value was below product plus freight value.

## Stage 3: Add Operational Context

The analysis then looked at order status.

Delivered orders with payment value below product plus freight value were treated as a separate review group because the operational process showed the order as complete while the financial values did not fully reconcile.

This did not prove that the orders were unpaid.

It showed that more context was required.

## Stage 4: Use Instalment Detail to Prioritise Review

The delivered shortfall population was then separated using the recorded payment-instalment field.

This produced:

* single-instalment orders,
* multiple-instalment orders,
* and one delivered order with no instalment detail.

The purpose of this split was not to prove which orders were genuinely outstanding.

It was to identify which records might require earlier review and which required additional payment context before any conclusion was reached.

---

# The Solution

The Power BI report was designed as a two-page reconciliation and decision-support case study.

## Page 1: Headline Reconciliation View

The first page establishes the overall position.

It shows:

* recorded payment value,
* product plus freight value,
* net reconciliation difference,
* product value,
* freight value,
* cancelled / unavailable order value,
* and the number of orders requiring reconciliation review.

The purpose of this page is to show that the headline difference alone is not enough.

The key finding is:

> The totals are close, but 1,158 individual orders still require explanation.

This creates the starting point for the second page.

## Page 2: Reconciliation Exception View

The second page breaks the exception population into categories.

It separates:

* payment values above product plus freight value,
* delivered orders where payment value is below product plus freight value,
* single-instalment delivered shortfalls,
* multiple-instalment delivered shortfalls,
* and missing instalment information.

This changes the reporting question from:

> How large is the difference?

to:

> What kind of difference is it, and what should be checked next?

The distinction is important because different exceptions may require different actions.

---

# Dashboard Highlights

## Headline Reconciliation Dashboard

The first page focuses on the overall financial comparison.

It includes:

* 16.01M recorded payment value
* 15.84M product plus freight value
* 0.17M net reconciliation difference
* 13.59M product value
* 2.25M freight value
* 0.10M cancelled / unavailable order value
* 1,158 reconciliation-review orders

The headline finding was:

> Recorded payment value is higher than product plus freight value, but the net difference does not tell the whole story.

Positive and negative order-level differences partly offset each other.

That means a relatively small total difference can still hide a meaningful volume of reconciliation work.

## Reconciliation Exception Dashboard

The second page focuses on where the difference sits.

### Payment Value Above Product Plus Freight Value

The analysis identified:

* 1,066 orders
* 165.66K positive reconciliation difference
* 155.41 average positive difference per order

These records show where recorded payment value exceeds product plus freight value.

The dataset does not provide enough evidence to confirm that these are genuine customer overpayments.

They are therefore treated as reconciliation exceptions requiring explanation.

### Delivered Orders with Payment Value Below Order Value

The analysis also identified:

* 91 delivered orders
* 343.05 delivered payment shortfall value

These orders require a different review because the operational process shows them as delivered while the recorded payment value remains below product plus freight value.

Again, the dataset does not prove that these orders are genuinely unpaid.

The value of the analysis is in identifying the exception and directing attention to the records that need further context.

### Instalment Detail

The delivered shortfall group was split further.

Single instalment:

* 35 orders
* 76.67 shortfall value

Multiple instalments:

* 55 orders
* 122.92 shortfall value

No instalment detail:

* 1 order
* 143.46 shortfall value

This helps distinguish between records that may warrant earlier review and records where the payment structure provides additional context.

---

# Key Findings

The analysis identified several important findings.

## 1. Headline Totals Can Hide Order-Level Exceptions

The overall net reconciliation difference was relatively small compared with total transaction value.

However, 1,158 orders contained individual differences.

This demonstrates why reconciliation should not stop at the grand total.

A total can reconcile reasonably well while many individual transactions still require review.

## 2. Positive and Negative Differences Should Not Be Treated as One Group

The exception population contained both:

* payment values above product plus freight value;
* and payment values below product plus freight value.

These are different reconciliation questions.

They may have different causes and should not automatically be assigned the same review process.

## 3. Delivered Shortfalls Require More Context

A delivered order with payment value below product plus freight value deserves attention because the operational process appears complete.

However, the available data does not show:

* confirmed cash collection,
* receivables,
* settlement timing,
* refunds,
* credits,
* chargebacks,
* or financing arrangements.

The dashboard therefore identifies the question but does not claim to prove the cause.

## 4. Payment Structure Can Help Prioritise Review

The payment-instalment field provides useful context.

Single-instalment shortfalls may warrant earlier review because the payment structure does not immediately explain the difference.

Multi-instalment records need additional context before being treated as an issue.

The field helps prioritise review.

It does not prove payment status.

## 5. Missing Data Creates Decision Risk

One delivered shortfall order had no usable instalment detail.

That is a small number of records, but the issue is important.

Missing information makes the transaction harder to interpret at exactly the point where someone needs to decide what action to take.

Data completeness therefore matters not only for reporting quality, but for operational confidence.

---

# Operational Recommendations

The analysis led to five practical recommendations.

## 1. Agree Shared Reporting Definitions

Finance and operations should agree what terms such as:

* product value,
* order value,
* payment value,
* completed value,
* outstanding value,
* and reconciliation difference

actually mean.

A shared dashboard does not solve the problem if different teams still attach different meanings to the same measure.

## 2. Monitor Reconciliation at Order Level

Headline totals should be supported by order-level exception monitoring.

At minimum, the reporting process should distinguish between:

* reconciled orders,
* payment value above order value,
* payment value below order value,
* delivered shortfalls,
* and incomplete payment information.

This prevents positive and negative differences from disappearing into a net total.

## 3. Prioritise Exceptions Based on Context

Not every reconciliation difference needs the same response.

Useful review groups include:

* delivered shortfalls with a single instalment,
* delivered shortfalls with multiple instalments,
* records with missing instalment information,
* high-value positive differences,
* and cancelled or unavailable orders still carrying value.

This creates a more useful review queue than a single list of mismatched orders.

## 4. Improve Data Validation and Completeness

Fields required for financial interpretation should be complete where the business process allows it.

Useful controls could include:

* mandatory payment-detail fields,
* validation of instalment values,
* warnings for missing payment information,
* reconciliation checks between payment and order values,
* and exception flags for unusual combinations of order status and payment value.

The aim is not simply to clean data later.

It is to reduce uncertainty at the point where the record is created.

## 5. Add Finance-System Context

To move from reconciliation exception to confirmed financial position, the reporting model would need additional information such as:

* invoice records,
* settlement dates,
* refunds,
* credit notes,
* receivables,
* chargebacks,
* payment-provider data,
* and financing information.

Without those sources, the analysis can show where the questions sit.

It cannot fully answer them.

---

# Data Limitations

This case study uses a public ecommerce dataset and should not be treated as a complete finance-system audit.

The available data does not prove:

* unpaid debt,
* confirmed customer overpayments,
* failed collections,
* incorrect accounting,
* fraud,
* or settlement status.

The `payment_installments` field provides information about the recorded payment structure, but it does not confirm which instalments have been collected or remain outstanding.

The analysis therefore uses the language of:

* reconciliation difference,
* shortfall,
* positive difference,
* exception,
* and review requirement.

It avoids treating those differences as confirmed accounting outcomes.

The most useful conclusion is:

> The dataset shows where finance and operations need more context before they can rely on the same number for the same decision.

---

# Demo

The repository includes the case study assets used to demonstrate the analysis.

Suggested walkthrough order:

1. Review the source dataset information
2. Review the Power BI data model
3. Review the DAX measures
4. Open the headline reconciliation page
5. Review the order-level exception analysis
6. Review the delivered shortfall categories
7. Read the final case study PDF
8. Review the operational recommendations

---

# How to Run

## Requirements

* Power BI Desktop
* Brazilian E-Commerce Public Dataset by Olist

## Steps

1. Download or clone the repository

```bash
git clone <repository-url>
```

2. Download the Olist ecommerce dataset

The model uses the relevant order, order-item, payment, product and customer files.

3. Open the Power BI file

Open the `.pbix` file in Power BI Desktop.

4. Check the source-file paths

If required, update the Power Query source paths so that they point to the location of the downloaded CSV files.

5. Refresh the model

Refresh the Power BI report to load the source data.

6. Review the report pages

Start with:

* **Which version of order value are we using?**
* **Where does the reconciliation difference sit?**

7. Review the case study PDF

Use the PDF summary alongside the Power BI report to follow the business reasoning and recommendations.

---

# Suggested Business Use

This case study demonstrates how a business can move from a headline financial comparison to a more useful reconciliation process.

It is relevant where managers need to understand:

* why finance and operations report different values,
* whether order and payment values reconcile,
* where exceptions are concentrated,
* which records need earlier review,
* whether missing information limits confidence,
* and what additional finance-system data is required before conclusions can be made.

The project also demonstrates why reporting should not stop when the headline number looks reasonable.

The first question was whether the totals matched.

The more useful question was what the differences underneath them meant.

That is where reporting becomes decision support.

---

# Tools Used

* Power BI Desktop
* Power Query
* DAX
* Brazilian E-Commerce Public Dataset by Olist
* GitHub
* PDF case study export

---

# Project Status

Completed as a portfolio case study.

Potential future improvements include:

* adding confirmed settlement data,
* adding invoice and receivables information,
* modelling refunds and credits,
* adding payment-provider reconciliation,
* introducing a formal exception-priority workflow,
* and testing the same reporting logic against ERP or SAP Business One data where permitted.
