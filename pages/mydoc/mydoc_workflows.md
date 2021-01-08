---
title: Workflows
sidebar: mydoc_sidebar
permalink: workflows.html
folder: mydoc
---

**Introduction**

You can use our NDC JSON API to search tickets, create orders, issue tickets, add services...

Using our NDC JSON API, you can book and issue tickets, and adding ancillaries to these bookings too.

You can find our basic workflows here:

- [Booking]({{  page.url | remove:'/workflows.html' | split: '/'  }}/booking.html/)
- [Servicing]({{  page.url | remove:'/workflows.html' | split: '/'  }}/servicing.html/)

---

**Methods**

You can find our NDC JSON API docs [here](https://api.airgateway.net/v1.1/swagger-ui/).

Anyway, below you have a little description on what these methods are used for.

---

**_AirShopping_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/AirDocIssue_Post) and [an example](https://docs.airgateway.net/?version=latest#2e6c3925-7fc9-4675-a633-4e218762e98d) on how to use this method.

This method receives a "search" with the flights info you want to search (origin, destination, dates...) and you'll receive a list of offers of each of the airlines you send the request to (you can indicate this via headers as [explained here](https://dev-guides.airgateway.net/getting_started/sending_requests_to_our_ndc_api/)).

---

**_OfferPrice_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OfferPrice_Post) and [an example](https://docs.airgateway.net/?version=latest#e6a12080-535a-4083-81d3-ece0841aeffd) on how to use this method.

This method receives the id of an offer you want to see detailed (you'll get a list of offer ids in AirShopping) and will return the information the airline gives us for that given offer. Please have in mind that details can be different from an airline to another (some airlines send really exhaustive disclosures while others only send some raw texts, for example). Some airlines don't even implement this method so we'll return the information we have for that offer from AirShopping.

---

**_OrderCreate_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderCreate_Post) and [an example](https://docs.airgateway.net/?version=latest#57433cd3-b160-4a35-8e7a-a465c8d5b96e) on how to use this method.

This method receives the information about the offer you want to buy and information essential to create the order (passengers info).

You can send payment information here too, but it's not recommended for most of the airlines and usecases. If you send payment information, some airlines will try to auto-issue the tickets immediately, which can lead to errors sometimes (if you have infants in your order, for example, you'll have to wait for confirmation from the airline first).

Sometimes it's needed to add the form of payment because airline doesn't allow order reservation for that offer. For example with Iberia you need to pay when you want to buy tickets for a flight departing today. In vueling paying when creating the order is the default option.

---

**_OrderRetrieve_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderRetrieve_Post) of this method.

This method receives the ID of the order you want to retrieve and returns all the information attached to that order.

You'll need to call this method if you want to check the status before you go ahead with AirDocIssue, for example.

You'll receive all order details, everything we receive from the airline and some information we store in our databases like disclosures received in the OfferPrice or remarks and comments your agents can add.

---

**_AirDocIssue_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/AirDocIssue_Post) of this method.

This method will receive the payment method details and the order id you want to pay and get the tickets.

You'll receive all order details, including tickets information, everything we receive from the airline and some information we store in our databases like disclosures received in the OfferPrice or remarks and comments your agents can add.

---

**_SeatAvailability_**

[This method](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/SeatAvailability_Post) allows you to request available seats in a given offer. When it's done before you book the order (pre-booking) you'll have to add the payment method (and pay) in OrderCreate to succeed (for example with Iberia).

Sometimes even airlines which accept this method will return an error with some offers (not all flights and fares accept seat selection).

---

**_OrderRetrieve_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderRetrieve_Post) of this method.

This method receives the ID of the order you want to retrieve and returns all the information attached to that order.

You'll need to call this method if you want to check the status before you go ahead with AirDocIssue, for example.

You'll receive all order details, everything we receive from the airline and some information we store in our databases like disclosures received in the OfferPrice or remarks and comments your agents can add.

---

**_OrderReshop_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderReshop_Post) of this method.

This method receives the ID of the order you want to retrieve some more info like "when" do you want to flight instead.

The response will include all the offers that match that new search, it's a kind of new _AirShopping_.

---

**_OrderReshopReprice_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderReshopReprice_Post) of this method.

It's more or less like OrderPrice in Reshop. You'll receive details about an offer to change your current order.

---

**_OrderChange_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderChange_Post) of this method.

This method is called to "save changes" after a change (like OrderReshop, adding seats or services). You'll need to send different information depending on the action you're performing (you'll need to send the ReshopOffferID if you're changing dates but you'll have to send Services if you're adding services, for example), as long as other general data like form of payment and so on.

You'll receive a response with the Order details like after OrderCreate.

---

**_SeatAvailability_**

[This method](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/SeatAvailability_Post) allows you to request available seats in a given offer. When it's done before you book the order (pre-booking) you'll have to add the payment method (and pay) in OrderCreate to succeed (for example with Iberia).

Sometimes even airlines which accept this method will return an error with some offers (not all flights and fares accept seat selection).

---

**_ServiceList_**

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/ServiceList_Post) of this method.

This service receives information about the passengers so the airlines can know what Services are available depending on the type of passenger (age) and returns a list of services with description, prices, taxes...
