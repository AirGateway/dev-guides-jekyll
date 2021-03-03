---
title: Webhooks
sidebar: mydoc_sidebar
permalink: webhooks.html
folder: pages
---

We offer some event based services like mails or slack notifications after orders are created, changes in orders or orders are canceled. We can personalize some of these services if needed, but we offer a really versatile service you can use to be notified on every event you want to track: **webhooks**.

We currently track these events:

- OrderCreated
- OrderCanceled
- OrderTicketed
- OrderStarted (Time of first flight has passed)
- OrderCompleted (Time of last flight has passed)
- ItineraryChange
- ServicesAddition
- ServicesRemoval
- SeatsAddition
- SeatsRemoval

For each of these events, we can call any endpoint you want (we can use the same for all events or we can call a different one for each).

Everytime the selected events are triggered, we'll call your endpoint with a JSON body including the information you need. This is **completely configurable**, we can adapt it to your needs, using any of these fields:

- **agwID**: Order id in our platform
- **orderID**: Order id from airline
- **pnr**
- **recordLocator**
- **bookingType**: One Way, Round Trip or Multicity
- **origin**
- **destination**
- **fullPath**: All legs in the order (MAD-LHR, LHR-MAD...)
- **adultsPax**: number of adults
- **childrenPax**: number of children
- **infantsPax**: number of infants
- **orderStatus**: cancelled, on hold...
- **totalAmount**
- **createdOn**
- **updatedOn**
- **sessionId**
- **agentEmail**: email from the agent that triggered the event
- **consumerEmail**: email from the consumer in the order
- **psgPhone**: contact passenger phone
- **psgEmail**: contact passenger email
- **consumerIataCode**
- **consumerCountryCode**
- **consumer**: consumer name
- **provider**: provider code
- **agent**: agent name
- **agency**: agency name

For example we can configure a task to call your endpoints on OrderTicketed with this information:

```
{
    "httpRequest": {
        "url": "https://yourservices/api/order-ticketed",
        "header": {
            "authorization": "Basic YourPassword"
        },
        "jsonBody": {
            "orderID": "{{agwID}}",
            "agent": "{{agent}}",
            "agency": "{{agency}}",
            "pnr": "{{pnr}}",
            "freeText": "Order has been ticketed, this is your order ID: {{agwID}}"
        }
    }
}
```
