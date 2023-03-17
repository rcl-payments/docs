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

- Then, click on the **Generate an API Key** button

- Copy the value of the **Subscription Id** and **API Key** that was generated to make authorized requests to the Payment API

## Use the API Key to Make a Request

To make a request to the Payment API, include the API Key as a `Bearer` **Authorization** token in the header of the request

### Example

```bash
POST /paymentrequest/subscriptionid/s45vdyegf233-g5674-34rwe-34rd-657yger456/create
Host: https://rclapi.azure-api.net/production/v7/payment
Authorization: Bearer sergeve456-e5467-45er-y456-5476fgdrst56
```

## Base URI

The base URI for the **live** version of the Payment API is :

```bash
https://rclapi.azure-api.net/production/v7/payment
```

The base URI for the **sandbox** version of the Payment API is :

```bash
https://rclapi.azure-api.net/development/v7/payment
```

## API Endpoint

The endpoint for the Payment API is :

```bash
/paymentrequest/subscriptionid/{subscrid}/create
```

where the placeholder : {subscrid} is the **Subscription Id** of the subscription id you generated from the authorization API Key previously.

## Request Method

A **POST** request has to be made to the API endpoint.

## Request Body

The request body should include a JSON of a **PaymentRequest** object.

| Parameter | Description | Type | Required
| --- | --- |--- |
| currency |Lower case currency code | string | Yes 
| amount |The payment amount | decimal | Yes
| orderId |A parameter supplied by the subscriber to track payment | string | Yes
| webappId |The id of the web app registered by the supplier in the portal  | integer | No
| paymentLink |The html payment link returned by the Payment API | string | No

### Example PaymentRequest object

```json
{
    "currency" : "usd",
    "amount" : 5.00,
    "orderId":"ord-12|cus-23",
    "webappId":17
}
```

Notes :

- The orderId is provided by the subscriber to track the payment with one or more parameters in its own systems.
- The Web App is registered by the subscriber in the portal to specify the URL where the buyer is returned after the purchase. [Learn about WEb App]().

### Example Request

```bash
POST /production/v7/payment/paymentrequest/subscriptionid/s45vdyegf233-g5674-34rwe-34rd-657yger456/create HTTP/1.1
Host: rclapi.azure-api.net
Authorization: Bearer sergeve456-e5467-45er-y456-5476fgdrst56
Content-Type: application/json
Content-Length: 102

{
    "currency" : "usd",
    "amount" : 5.00,
    "orderId":"ord-12|cus-23",
    "webappId":17
}
```

# Response

## 200 Ok

This represents success in making an authorized request to the Payment API and returns a **PaymentRequest** object in JSON format in the **body** of the response. 

## 401 Unauthorized

The authorization failed for the request. Check the body of the response for additional error details in ``text/plain`` format.

## 400 Bad Request

An error occurred while processing the request. Check the body of the response for additional error details in ``text/plain`` format.

## Example Response Body

```json
{
    "Id": 1,
    "dateCreated": "2023-03-17T22:23:01.2042245+00:00",
    "subscriptionId": 87,
    "currency": "usd",
    "amount": 5.00,
    "orderId": "ord-12|cus-23",
    "paymentLink": "https://payment.rclapp.com/Payment/CheckoutSession/Create?code=cdfg456-gtf34-gf45-tger-hdtte5693745g",
    "code": "cdfg456-gtf34-gf45-tger-hdtte5693745g",
    "webappId": 17
}
```

# Using the Payment Link

The Payment API will return a html payment link in the response within the **PaymentRequest** object.

The subscriber can then place this link on their website or online application to process a payment with Stripe when the link is clicked by a buyer.

**The payment link will expire in 24 hrs**.

The image below illustrates the Stripe payment page when the link is clicked.

![Stripe Payment Page](/images/api-stripe-payment-page.png)