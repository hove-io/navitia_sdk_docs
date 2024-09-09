---
title: Schedule Screens - Navitia SDK Docs
---

# Schedule Screens

## Screen flow

Refer to the following schema to learn more about different interactions and how to navigate between module screens:

<div style="text-align: center">
``` mermaid
graph TB
    Lines(Lines) --> Search(Search)
    Lines(Lines) --> Timetable(Timetable)
    Search(Search) --> Stations(Stations)
    Lines(Lines) --> Stations(Stations)
    Search(Search) --> Timetable(Timetable)
    Stations(Stations) --> Timetable(Timetable)
```
</div>

## Lines

The lines screen allows the user to see all the lines of the defined coverage. The lines are sorted by the different configurable transport categories.<br>
Another filter is added for each transport mode in the selected transport category. 

The lines can also be grouped by networks. To enable this feature, you need to switch the `transport_networks` parameter to `true` in the [features configuration](../../getting_started/#schedule-features). 

=== "Android"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_home_screen.png" alt="Lines screen">

=== "iOS"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_home_screen.png" alt="Lines screen">

If there is any favorite station, an additional tab will be shown listing all bookmarked stations. Each station has a maximum of 3 next departures by destination or an empty state if data is unavailable.

=== "Android"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_home_favorites_screen.png" alt="Lines screen with favorites">

=== "iOS"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_home_favorites_screen.png" alt="Lines screen with favorites">

## Search

The search screen allows the user to seek for a station or a line using a built-in autocompletion. The result is based on the user search input text.<br>
The station result combines both the name of the station and all the lines passing through that station. This will allow the user to select directly the searched line and get the list of all destinations starting from the target station point.<br>

A history feature is added to this screen, allowing the user to choose from the previous selected items. The `maxHistory` parameter defines the maximum number of items to show in the history list.

=== "Android"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_search_screen.png" alt="Search screen">

=== "iOS"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_search_screen.png" alt="Search screen">

## Stations

The station screen lists all the stations of the selected line alphabetically sorted. A search feature is added to filter the lines and makes it easier for the user to search for the desired station.<br>
In case the `directions_first` parameter is set to `true` in the [features configuration](../../getting_started/#schedule-features), this screen will show all stations of a defined route (destination).

=== "Android"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_line_stations_screen.png" alt="Stations screen">

=== "iOS"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_line_stations_screen.png" alt="Stations screen">

## Timetable

This screen allows the user to see the next departures of the target transport mode through the selected station which is heading to the chosen destination. The map gives more details about the vehicle journey by drawing the line path and both selected station and destination markers.<br>

=== "Android"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_station_next_departures_screen.png" alt="Next departures screen">

=== "iOS"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_station_next_departures_screen.png" alt="Next departures screen">

The user can also bookmark this selected station by taping the Favorite button on the bottom-right corner of the map. To enable this feature, you need to switch the `bookmark_mode` parameter to `true` in the [features configuration](../../getting_started/#schedule-features). 

=== "Android"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_station_next_departures_favorites_screen.png" alt="Next departures screen with favorite">

=== "iOS"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_station_next_departures_favorites_screen.png" alt="Next departures screen with favorite">

When the user taps on the All schedules button in the [next departures](#next-departures) screen, the all schedules screen shows up and gives all theoretical departures of the selected line from the selected station to the target destination.<br>

This screen includes a datepicker button allowing the user to choose a date and see all the scheduled departures on that date.

=== "Android"
    
    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_android_all_schedules_screen.png" alt="All schedules screen">

=== "iOS"

    <img class="img-overview" src="/navitia_sdk_docs/assets/img/schedule_ios_all_schedules_screen.png" alt="All schedules screen">
