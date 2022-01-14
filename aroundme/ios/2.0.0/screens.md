---
layout: main
title: Screens
parent: Around Me iOS
grand_parent: Around Me
nav_order: 3
permalink: /aroundme/ios/screen
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

### Map

The map screen represents the main screen of this module. It shows the places close to the center of the visible region, draws them on the map and adds them to the bottom sliding panel.\
The shown data depend on the selected elements in the [filters](#filters) screen.

<img src="{{ site.baseurl }}/assets/img/aroundme_ios_map_screen.png" alt="Map screen" width="250"/>

### Search

The search screen allows the user to seek for a place using a built-in autocompletion. The result is a selection of addresses, stations and points of interest based on the user search input text.\
If an element is selected, this screen will disappear and the map will be centered over the selected item location.
Please note that a history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

<img src="{{ site.baseurl }}/assets/img/aroundme_ios_search_screen.png" alt="Search screen" width="250"/>

### Filters

This screen content is a visual version of the passed filters configuration (check [getting started]({{ site.baseurl }}/aroundme/ios/getting-started/#filters) page for more information). The selected elements will be used to filter the data received and drawn within the map. One filter should at least be selected or else the user can't apply the current filters configuration.\
If you want to reset the user filters configuration, you can simply call `AroundMeUI.getInstance().resetUserPreferences()` and the current configuration will be deleted and the screen will be updated according to the new passed configuration.

<img src="{{ site.baseurl }}/assets/img/aroundme_ios_filters_screen.png" alt="Filters screen" width="250"/>

## Navigating

Please refer to the following schema to learn more about different interactions and how to navigate between module screens.

<img src="{{ site.baseurl }}/assets/img/aroundme_ios_navigating.png" alt="Navigating screen" width="950"/>

