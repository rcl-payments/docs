---
title: Payment API
description: RCL Payments use the Payment API to request online payment processing from stripe
has_children: false
nav_order: 5
---

# Payment API
**V7**

A subscriber will use the *Payment API* to make a request for [Stripe](https://stripe.com) to process an online Credit Card payment.

## How it works

A POST request is made to the Payment API endpoint with a payload containing the details of the payment to be processed. 

A response in returned with a html link to process the payment contained in an object returned in the response.

The link is displayed on the subscriber's web site or online application for the buyer to click to complete the payment.

## Authorization

An API Key is required to make requests to the Payments API. To obtain a key follow these steps :

- In the RCL Payments Portal, in the side menu click on **Account > API Key**

- In the **API Key** page, click on the **Register an API Key** button

- 