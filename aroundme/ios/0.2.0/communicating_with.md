---
layout: default
title: Communicating with
parent: Around Me iOS
grand_parent: Around Me
nav_order: 4
permalink: /aroundme/ios/communicating-with
---

# Communicating with

---

## Journey

This module communicates with [Journey]({{ site.baseurl }}/journey/) module in order to get directions for a chosen itinerary. You should enable the `Go from/Go to` feature when first initializing the module by setting `enableGoFromGoTo` to `true` in `AroundMeConfiguration`.\
Please refer to the code below to initialize the `Router` module since it's mandatory to build the connection between these modules:

```swift
try Router.shared
          .register(journey: JourneySdk.shared.journeyRouter)
          .register(aroundMe: AroundMe.shared.aroundMeRouter)
          .register(app: self)
          .initialize()
```

When the user taps on a marker on the map, the buttons `Go from` and `Go to` should pop up as follows:

<img src="{{ site.baseurl }}/assets/img/aroundme_ios_go_fromto.png" alt="Map screen" width="250"/>

Clicking on one of the buttons will redirect the user to Journey module with the given origin/destination.
