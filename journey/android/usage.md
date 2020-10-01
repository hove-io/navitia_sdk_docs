---
layout: default
title: Usage
parent: Journey Android
grand_parent: Journey
nav_order: 2
permalink: /journey/android/usage
---

# Usage

---

## Journeys request
| Parameters | Type | Required | Description | Example |
| --- | --- |:---:| --- | --- |
| `.setOriginId()` | `String` | ✓ | Origin coordinates, following the format `lon;lat` | `"2.3665844;48.8465337"` |
| `.setDestinationId()` | `String` | ✓ | Destination coordinates, following the format `lon;lat` | `"2.2979169;48.8848719"` |
| `.setOriginLabel()` | `String` | ✗ | Origin label, if not set the address will be displayed | `"Home"` |
| `.setDestinationLabel()` | `String` | ✗ | Destination label, if not set the address will be displayed | `"Work"` |
| `.setDatetime()` | `DateTime` | ✗ | Requested date and time for journey results | `DateTime.now()` |
| `.setDatetimeRepresents()` | `Enum` | ✗ | Can be `.DEPARTURE` (journeys after datetime) or `.ARRIVAL` (journeys before datetime). | `JourneysRequest.DEPARTURE` |
| `.setForbiddenUris()` | `List<String>` | ✗ | Used to avoid lines, modes, networks, etc in the Journey search (List of navitia uris) | `Arrays.asList("commercial_mode:Bus", "line:1")` |
| `.setAllowedId()` | `List<String>` | ✗ | If you want to use only a small subset of the public transport objects in the Journey search (List of navitia uris) | `Arrays.asList("commercial_mode:Bus", "line:1")` |
| `.setFirstSectionModes()` | `List<String>` | ✗ | List of modes to use at the begining of the journey | `Arrays.asList("walking", "bike", "car", "bss", "ridesharing")` |
| `.setLastSectionModes()` | `List<String>` | ✗ | List of modes to use at the end of the journey | `Arrays.asList("walking", "bike", "car", "bss", "ridesharing")` |
| `.setCount()` | `Integer` | ✗ | The number of journeys that will be displayed | `3` |
| `.setMinNbJourneys()` | `Integer` | ✗ | The minimum number of journeys that will be displayed | `3` |
| `.setMaxNbJourneys()` | `Integer` | ✗ | The maximum number of journeys that will be displayed | `10` |
| `.setAddPoiInfos()` | `List<String>` | ✗ | Allow the display of the availability in real time for bike share and car park | `Arrays.asList("bss\_stands", "car\_park")` |
| `.setDirectPath()` | `String` | ✗ | To indicate if the journey is direct | `"only"` |


## Tranport Mode
| Parameters | Type | Required | Description | Example |
| --- | --- |:---:| --- | --- |
| title | `String` | ✓ | The transport mode label | "Tramway" |
| textIcon | `String` | ✓ | The transport mode Icon | "\uEA1B" |
| firstSectionMode | `List<String>` | ✗ | List of modes to use at the begining of the journey | { "walking", "bike", "car", "bss", "ridesharing" } |
| lastSectionMode | `List<String>` | ✗ | List of modes to use at the end of the journey | { "walking", "bike", "car", "bss", "ridesharing" } |
| physicalModes | `List<String>` | ✗ | Used setup lines, modes, networks, etc in the Journey search (List of navitia uris) | { "physical_mode:Bike", "physical_mode:Train" } |
| realTime | `Boolean` | ✗ | To indicate if real time is enabled | false |
| selected | `Boolean` | ✗ | To indicate if the transport mode is selected | true |

### Setup Transport Modes List

#### Example

##### Get available Transport Mode List for selected Coverage from Navitia:
```ruby
https://api.navitia.io/v1/coverage/<COVERAGE>/physical_modes?
```

###### Build Transport Modes List:
```java
private ArrayList<TransportModeModel> getTransportModes() {
    ArrayList<TransportModeModel> transportModes = new ArrayList<>();
    transportModes.add(new TransportModeModel(TransportMode.BUS)
        .setFirstSectionMode(SECTION_MODE_WALKING)
        .setLastSectionMode(SECTION_MODE_WALKING)
        .setPhysicalModes("physical_mode:Bus")
        .setSelected(true));

    transportModes.add(new TransportModeModel(TransportMode.BIKE)
        .setFirstSectionMode(SECTION_MODE_BIKE)
        .setLastSectionMode(SECTION_MODE_BIKE)
        .setPhysicalModes("physical_mode:Bike")
        .setSelected(false));

    transportModes.add(new TransportModeModel(TransportMode.CAR)
        .setFirstSectionMode(SECTION_MODE_CAR)
        .setLastSectionMode(SECTION_MODE_CAR)
        .setPhysicalModes("physical_mode:Car")
        .setSelected(true));

    return transportModes;
}
```

##### With form
The user access the search parameters (date, time, departure, arrival, transport mode)
and can change the search parameters
and must validate the form before accessing journeys list

```java
final Intent intent = new Intent(v.getContext(), FormActivity.class);

final JourneysRequest request = new JourneysRequest("fr-idf");
request.setOriginLabel("My Home")
       .setOriginId("2.3665844;48.8465337")
       .setDestinationId("2.2979169;48.8848719")
       .setAddPoiInfos(Arrays.asList("bss_stands", "car_park"))
       .setCount(5)
       .setTransportModeListRequested(getTransportModes());

FragmentTransaction ft = getFragmentManager().beginTransaction();
FormFragment formFragment = FormFragment.newInstance(request);
ft.replace(R.id.activity_main_content, formFragment, FragmentTag.FORM_FRAGMENT);
ft.addToBackStack(FragmentTag.FORM_FRAGMENT);
ft.commit();
```

##### Without form
The user Cannot change the search parameters
and the journeys list appears directly

```java
final Intent intent = new Intent(v.getContext(), JourneysActivity.class);

final JourneysRequest request = new JourneysRequest("fr-idf");
request.setOriginLabel("My Home")
       .setOriginId("2.3665844;48.8465337")
       .setDestinationId("2.2979169;48.8848719")
       .setAddPoiInfos(Arrays.asList("bss_stands", "car_park"))
       .setCount(5);

FragmentTransaction ft = getFragmentManager().beginTransaction();
JourneysFragment journeysFragment = JourneysFragment.newInstance(request);
ft.replace(R.id.activity_main_content, journeysFragment, FragmentTag.JOURNEYS_FRAGMENT);
ft.addToBackStack(FragmentTag.JOURNEYS_FRAGMENT);
ft.commit();
```

##### Public transport 

```java
final JourneysRequest request = new JourneysRequest("fr-idf");
```

##### Bike

```java
final JourneysRequest request = new JourneysRequest("fr-idf");
request.setOriginId("2.3665844;48.8465337")
       .setDestinationId("2.2979169;48.8848719")
       .setFirstSectionModes(Arrays.asList("bike"))
       .setLastSectionModes(Arrays.asList("bike"))
       .setForbiddenUris(Arrays.asList("physical_mode:Bus", "physical_mode:Tramway", "physical_mode:Metro"));
```

##### BSS

```java
final JourneysRequest request = new JourneysRequest("fr-idf");
request.setOriginId("2.3665844;48.8465337")
       .setDestinationId("2.2979169;48.8848719")
       .setFirstSectionModes(Arrays.asList("bss"))
       .setLastSectionModes(Arrays.asList("bss"))
       .setForbiddenUris(Arrays.asList("physical_mode:Bus", "physical_mode:Tramway", "physical_mode:Metro"))
       .setAddPoiInfos(Arrays.asList("bss_stands"));
```

##### Car

```java
final JourneysRequest request = new JourneysRequest("fr-idf");
request.setOriginId("2.3665844;48.8465337")
       .setDestinationId("2.2979169;48.8848719")
       .setFirstSectionModes(Arrays.asList("car"))
       .setAddPoiInfos(Arrays.asList("car_park"));
```

##### Ridesharing

```java
final JourneysRequest request = new JourneysRequest("fr-idf");
request.setOriginId("2.3665844;48.8465337")
       .setDestinationId("2.2979169;48.8848719")
       .setFirstSectionModes(Arrays.asList("ridesharing"))
       .setLastSectionModes(Arrays.asList("ridesharing"));
```

## Override icons
To customize arrival, departure and transport mode icon, you need to add your vector asset in the `drawable/` folder of your application.
Rename your customized transport mode icon with the same resource name as the default icon.

### Departure Icon
In order to customize the `departure` icon, rename your resource as `ic_departure.xml`

### Arrival Icon
In order to customize the `arrival` icon, rename your resource as `ic_arrival.xml`

### Transport mode icons
You have 2 possibilities to customize the transport mode icon:

Setup programmatically:
```kotlin
TransportModeModel(TransportMode.BIKE).apply {
    ...
    resIconId = R.drawable.icon_id // <- Set your icon here
}
```

Override drawable resources:
Rename your customized transport mode icon with the same resource name as the default icon.
For example, in order to customize the `bus` icon, rename your resource as `ic_transport_mode_bus.xml`
Here is the list of default icon name:
* `ic_transport_mode_air.xml`
* `ic_transport_mode_bike.xml`
* `ic_transport_mode_bss.xml`
* `ic_transport_mode_bus.xml`
* `ic_transport_mode_car.xml`
* `ic_transport_mode_coach.xml`
* `ic_transport_mode_ferry.xml`
* `ic_transport_mode_funicular.xml`
* `ic_transport_mode_metro.xml`
* `ic_transport_mode_ridesharing.xml`
* `ic_transport_mode_shuttle.xml`
* `ic_transport_mode_taxi.xml`
* `ic_transport_mode_train.xml`
* `ic_transport_mode_tramway.xml`
* `ic_transport_mode_walking.xml`
