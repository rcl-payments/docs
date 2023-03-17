---
title: Introduction
description: The RCL Payments application allows organizations or users to accept online payments
has_children: false
nav_order: 1
---

# Introduction
**V7**

RCL Payments is a Software as a Services (SaaS) application available for subscription in the [Azure Marketplace]().

It allows organizations or users to accept online payments via a credit card on their website or an online application.

## How it works 
Payments are processed by [Stripe](https://stripe.com/) on the subscriber's web site or online application. The payments are forwarded to a proxy or intermediate US bank account. The subscriber will then transfer the funds from this bank account to their local bank account using [Wise](https://wise.com/). 

## Who is this application for

This application is for anyone accepting online payments. It is especially useful for those that do not have a US,UK,EU, etc. bank account or business that qualifies for Stripe registration.

An intermediate or proxy US bank account held by RCL Global LLC is used to temporarily hold funds so that you do no need to register a US/UK/EU etc. business and bank account to accept online payments. You can automatically withdraw funds from this account to your local bank account. The funds as wire transferred in US dollars using SWIFT to your local bank account. You will pay an operating fee of 10% of the transfer amount for these service.


# Getting Started

- [Subscribe](https://common.docs.rclapp.com/subscription/subscription.html) for the SaaS application in the Azure Marketplace
- Get the [Representative](./representative/representative.md) approved
- Get your Organization approved, if required
- Configure your payments
- Use the Payment API to add payments to your website or online application
- Check your online transactions
- Generate Payouts and transfer funds to your local bank account

# Testing

A [Sandbox Application]() is provided for subscriber's to design and test their payment integrations before going live. This sandbox application comprises both a *Web User Interface* to configure the payment system and an *API* to simulate online payments. It is highly recommended that subscribers use this sandbox to test their payment integrations before accepting live payments online.


