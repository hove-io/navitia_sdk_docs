---
layout: main
title: Screens
parent: Journey iOS
grand_parent: Journey
nav_order: 2
permalink: /journey/ios/screens
---

# Screens
{: .no_toc }

---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Screens

### Form

This screen shows different options for the user to define his itinerary. A set of options is available including departure and arrival fields, transport modes, profiles, walking speed and journey datetime configuration.

The form screen can be configured as an entry point of the SDK. You just need to set the `JourneySdk.shared.formJourney` to `true`.
Please note that the transport modes can be configured as explained in the section [transport mode]({{ site.baseurl }}/journey/ios/getting-started#transport-mode) from Getting Started page.

<img src="{{ site.baseurl }}/assets/img/journey_ios_form_screen.png" alt="Form screen" width="250"/>

### Autocompletion

In this screen, the user can choose the departure and the arrival of his itinerary. While typing in the target field, a list of options is shown below the field. The user can simply choose one of the suggested options and mark it as a departure or as an arrival point.

The suggested options are grouped in sections, it's whether a station, an address or a point of interest.
In this screen, a geolocation service is used to get the user location and translate it into a readable address. Therefore, another option is given and it allows the user to set his position as a departure or an arrival of the itinerary.

A history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

<img src="{{ site.baseurl }}/assets/img/journey_ios_autocompletion_screen.png" alt="Autocompletion screen" width="250"/>

### Journeys

The journeys screen is fundamental and offers the solutions to the user for the requested itinerary.
After defining all the required parameters, this screen will popup with multiple results combining public transport, personal bikes/cars, bike sharing systems and even ridesharing possibilities.

Each result gives the needed information to the user in order to plan his journey. He can check the duration, the suggested means of transport, the next departure datetimes and many other useful details. This combination of data, being served by [Navitia](http://doc.navitia.io) servers and translated into a comprehensible/user friendly interface, is perfectly shaped to the user profile and needs.

The [autocompletion](#autocompletion) screen is also accessible from this page along with other itinerary request parameters allowing the user to make in-screen changes without the need to go back to the [form](#form). In order to make it happen, you will need to set the parameter `JourneySdk.shared.advancedSearchMode`to `true` when first configuring the SDK (which is already set to `true` by default if the form is defined as an entry point).

You can enable the earlier/later feature using the `isEarlierLaterFeatureEnabled` parameter. When this feature is available, the user can request journeys with earlier or later departure/arrival for the same itinerary.

<img src="{{ site.baseurl }}/assets/img/journey_ios_journeys_screen.png" alt="Journeys screen" width="250"/>

### Ridesharing offers

This screen lists the different ridesharing offers for the selected journey. Regardless of the fact that the journey can propose a full ridesharing trip or a partial ride, the user can select among different third party offers. He has all the information needed to choose the best offer that fits his needs including the departure time, the available seats, the price and some data about the driver offering the ride.

<img src="{{ site.baseurl }}/assets/img/journey_ios_ridesharing_offers_screen.png" alt="Ridesharing offers screen" width="250"/>

### Roadmap

We believe that the user needs more useful details about his journey and that's where the roadmap screen comes in. In this page, the user gets a visual overview about the selected itinerary with a simple colorful drawing on a map. Departure and arrival markers are also shown on the map along with the user location and itinerary segments delimiters.

The screen also includes a draggable bottom sheet which offers a step-by-step journey sections. Each section is represented in a way that it makes it easier to the user to follow the given instructions. The user can follow a built-in navigation narrative system if choosing to walk, to drive his own car or even to ride his bike. The public transport section is also well detailed when it comes to explain to the user how to take different means of transport from the departure to the arrival point.

<img src="{{ site.baseurl }}/assets/img/journey_ios_roadmap_screen.png" alt="Ridesharing offers screen" width="250"/>

## Navigating

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img src="{{ site.baseurl }}/assets/img/journey_ios_navigating.png" alt="Navigating screen"/>
