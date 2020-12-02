---
layout: default
title: Communicating with
parent: Around Me Android
grand_parent: Around Me
nav_order: 4
permalink: /aroundme/android/communicating-with
---

# Communicating with

## Journey

This module communicates with [Journey]({{ site.baseurl }}/journey/) module in order to get directions for a chosen itinerary. You should enable the `Go from/Go fo` feature when first initializing the module by calling `AroundMeUI.getInstance().withGoFromGoTo()`.\
The `Router` module should be initialized also with the right parameters, please refer to the code below:

```kotlin
if (!Router.getInstance().isInit) {
    Router.getInstance()
        .register(aroundMe = AroundMeUI.getInstance().aroundMeActivityDelegate)
        .register(journey = JourneysUI.getInstance().activityDelegate)
        .init()
}
```

When the user taps on a marker on the map, the buttons `Go from` and `Go to` should pop up as follows:

<img src="{{ site.baseurl }}/assets/img/aroundme_android_go_fromto.png" alt="Map screen" width="250"/>

Clicking on one of the buttons will redirect the user to Journey module with the given origin/destination.
