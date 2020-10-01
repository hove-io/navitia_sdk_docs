---
layout: default
title: Usage
parent: Journey iOS
grand_parent: Journey
nav_order: 2
permalink: /journey/ios/usage
---

# Usage

---

## Configuration - AppDelegate

| Parameters | Type | Required | Description | Default |
| --- | --- |:---:| --- | --- |
| token | String | ✓ | Navitia token (generate a token on [navitia.io](https://www.navitia.io/))| ✗ |
| colorConfiguration | JourneyColorConfiguration | ✓ | To setup the colors of the UI tunnel | ✗ |
| applicationBundle | Bundle | ✗ | The application bundle is needed for icons customization | ✗ |
| formJourney | Boolean | ✗ | To display the journey form screen | false |
| advancedSearchMode | Boolean | ✗ | To enable advanced search mode | false (If `formJourney` is set to true, this is automatically switched to true) |
| maxHistory | Int | ✗ | To set the maximum number of history inputs for autocompletion  | 10 |
| multiNetwork | Boolean | ✗ | To enable the display of the network name in the roadmap  | false |
| isEarlierLaterFeatureEnabled | Boolean | ✗ | To use shortcuts for next and previous journeys | false |

### Color Configuration

The colors can be configured using both `UIColor` instances or hexadecimal color codes. The table below explains the usage of each configuration color:

| Color | Description |
| --- | --- |
| background | Colors the main views background |
| primary | Colors some highlighted labels  |
| origin | Colors the departure pin and roadmap view background |
| originIcon | Colors the departure pin, the `origin` value will be ignored |
| originBackground | Colors the departure roadmap view background, the `origin` value will be ignored |
| destination | Colors the arrival pin and roadmap view background |
| destinationIcon | Colors the arrival pin, the `destination` value will be ignored |
| destinationBackground | Colors the arrival roadmap view background, the `destination` value will be ignored |

### Example

```swift
class AppDelegate: UIResponder, UIApplicationDelegate {
    
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        do {
            let colorConfiguration = JourneyColorConfiguration(background: UIColor(red: 64.0/255, green: 149.0/255, blue: 142.0/255, alpha: 1),
            origin: UIColor(red: 0, green: 187.0/255, blue: 117.0/255, alpha: 1),
            destination: UIColor(red: 176.0/255, green: 3.0/255, blue: 83.0/255, alpha: 1))
            
            try NavitiaSDKUI.shared.initialize(token: "your_token", colorConfiguration: colorConfiguration)
            NavitiaSDKUI.shared.applicationBundle = Bundle.main
            NavitiaSDKUI.shared.formJourney = false
            NavitiaSDKUI.shared.advancedSearchMode = false
            NavitiaSDKUI.shared.maxHistory = 12
            NavitiaSDKUI.shared.isEarlierLaterFeatureEnabled = true
            NavitiaSDKUI.shared.multiNetwork = true
        } catch {
            print(String(format: "Journey SDK cannot be initialized! %@", error.localizedDescription))
        }
    }    
}
```

## Journeys request - ViewController

| Parameters | Type | Required | Description | Example |
| --- | --- |:---:| --- | --- |
| coverage | String | ✓ | Navitia coverage | "fr-idf" |
| originId | String | ✓ | Origin coordinates, following the format `lon;lat` | "2.3665844;48.8465337" |
| destinationId | String | ✓ | Destination coordinates, following the format `lon;lat` | "2.2979169;48.8848719" |
| originLabel | String | ✗ | Origin label, if not set the address will be displayed | "Home" |
| destinationLabel | String | ✗ | Destination label, if not set the address will be displayed | "Work" |
| datetime | Date | ✗ | Requested date and time for journey results | Date() |
| datetimeRepresents | String | ✗ | Can be `.departure` (journeys after datetime) or `.arrival` (journeys before datetime). | .departure |
| forbiddenUris | [String] | ✗ | Used to avoid lines, modes, networks, etc in the Journey search (List of navitia uris) | ["commercial_mode:Bus", "line:1"] |
| allowedId | [String] | ✗ | If you want to use only a small subset of the public transport objects in the Journey search (List of navitia uris) | ["commercial_mode:Bus", "line:1"] |
| allowedPhysicalModes | [String] | ✗ | List of allowed physical modes | ["physical_mode:Bus", "physical_mode:Metro"] |
| firstSectionModes | [Enum] | ✗ | List of modes to use at the begining of the journey | [.walking, .car, .bike, .bss, .ridesharing] |
| lastSectionModes | [Enum] | ✗ | List of modes to use at the end of the journey | [.walking, .car, .bike, .bss, .ridesharing] |
| count | Integer | ✗ | The number of journeys that will be displayed | 3 |
| minNbJourneys | Integer | ✗ | The minimum number of journeys that will be displayed | 3 |
| maxNbJourneys | Integer | ✗ | The maximum number of journeys that will be displayed | 10 |
| addPoiInfos | [Enum] | ✗ | Allow the display of the availability in real time for bike share and car park | [.bss\_stands, .car\_park] |
| directPath | Enum | ✗ | To indicate if the journey is direct | .only |
| dataFreshness | Enum | ✗ | To indicate if theoretical or realtime data are requested | .baseSchedule |
| travelerType | Enum | ✗ | To give extra information about the traveler state | .standard |

### Example (With journey form enabled)

```swift
class ViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()

        // Setup form modes buttons
        let metroButton = ModeButtonModel(title: "Metro",
                                          type: "metro",
                                          selected: true,
                                          firstSectionMode: ["walking"],
                                          lastSectionMode: ["walking"],
                                          physicalMode: ["physical_mode:Metro"])
        let busButton = ModeButtonModel(title: "Bus",
                                        type: "bus",
                                        selected: true,
                                        firstSectionMode: ["walking"],
                                        lastSectionMode: ["walking"],
                                        physicalMode: ["physical_mode:Bus"])
        let bikeButton = ModeButtonModel(title: "Bike",
                                         type: "bike",
                                         selected: false,
                                         firstSectionMode: ["bike"],
                                         lastSectionMode: ["bike"])
        let bssButton = ModeButtonModel(title: "BSS",
                                        type: "bss",
                                        selected: false,
                                        firstSectionMode: ["bss"],
                                        lastSectionMode: ["bss"],
                                        realTime: true)
        let carButton = ModeButtonModel(title: "Car",
                                        type: "car",
                                        selected: false,
                                        firstSectionMode: ["car"],
                                        lastSectionMode: ["car"],
                                        realTime: true)
        NavitiaSDKUI.shared.modeForm = [metroButton, busButton, bikeButton, bssButton, carButton]
        // Enable Journey form screen display
        NavitiaSDKUI.shared.formJourney = true
        
        // Get entry screen view controller instance
        if var journeyResultsViewController = NavitiaSDKUI.shared.rootViewController {
            let journeysRequest = JourneysRequest(coverage: "selected_coverage")
            journeyResultsViewController.journeysRequest = journeysRequest
            
            // Invoke the screen using a navigation controller
            if let journeyResultsViewController = journeyResultsViewController as? UIViewController {
                navigationController?.pushViewController(journeyResultsViewController, animated: true)
            }
        }
    }
}
```

### Example (With journey form enabled)

```swift
class ViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()

        // Get entry screen view controller instance
        if var journeyResultsViewController = NavitiaSDKUI.shared.rootViewController {
            // Init a set of parameters
            let journeysRequest = JourneysRequest(coverage: "selected_coverage")
            journeysRequest.originId = "2.3665844;48.8465337"
            journeysRequest.originLabel = "Home"
            journeysRequest.destinationId = "2.2979169;48.8848719"
            journeysRequest.destinationLabel = "Work"
            journeysRequest.firstSectionModes = [.walking, .car, .bike, .bss, .ridesharing]
            journeysRequest.addPoiInfos = [.bssStands, .carPark]
            journeysRequest.count = 5
            
            journeyResultsViewController.journeysRequest = journeysRequest
            
            // Invoke the screen using a navigation controller
            if let journeyResultsViewController = journeyResultsViewController as? UIViewController {
                navigationController?.pushViewController(journeyResultsViewController, animated: true)
            }
        }
    }
}
```

#### Public transport 

```swift
let journeysRequest = JourneysRequest(coverage: "selected_coverage")
journeysRequest.originId = "2.3665844;48.8465337"
journeysRequest.destinationId = "2.2979169;48.8848719"
```

#### Bike

```swift
let journeysRequest = JourneysRequest(coverage: "selected_coverage")
journeysRequest.originId = "2.3665844;48.8465337"
journeysRequest.destinationId = "2.2979169;48.8848719"
journeysRequest.firstSectionModes = [.bike]
journeysRequest.lastSectionModes = [.bike]
```

#### BSS

```swift
let journeysRequest = JourneysRequest(coverage: "selected_coverage")
journeysRequest.originId = "2.3665844;48.8465337"
journeysRequest.destinationId = "2.2979169;48.8848719"
journeysRequest.firstSectionModes = [.bss]
journeysRequest.lastSectionModes = [.bss]
journeysRequest.addPoiInfos = [.bssStands]
```

#### Car

```swift
let journeysRequest = JourneysRequest(coverage: "selected_coverage")
journeysRequest.originId = "2.3665844;48.8465337"
journeysRequest.destinationId = "2.2979169;48.8848719"
journeysRequest.firstSectionModes = [.car]
journeysRequest.addPoiInfos = [.car_park]
```

#### Ridesharing

```swift
let journeysRequest = JourneysRequest(coverage: "selected_coverage")
journeysRequest.originId = "2.3665844;48.8465337"
journeysRequest.destinationId = "2.2979169;48.8848719"
journeysRequest.firstSectionModes = [.ridesharing]
journeysRequest.lastSectionModes = [.ridesharing]
```

## Sample project

To run the sample project, clone the repo, and run `pod install` from the `NavitiaSDKUI_sample` directory first.

## Image resources customization 

Customizing transport mode icons and other resources is made possible. To use this feature, you should rename your image resource to match the resource name found below.

The following resources can be overridden:

### Section modes

| Mode | Resource name |
| --- | --- |
| Air | journey_mode_air |
| Bike | journey_mode_bike |
| BSS | journey_mode_bss |
| Bus | journey_mode_bus |
| Car | journey_mode_car |
| Coach | journey_mode_coach |
| Crow fly | journey_mode_crow_fly |
| Ferry | journey_mode_ferry |
| Funicular | journey_mode_funicular |
| Metro | journey_mode_metro |
| Rapid transit | journey_mode_rapidtransit |
| Ridesharing | journey_mode_ridesharing |
| Shuttle | journey_mode_shuttle |
| Taxi | journey_mode_taxi |
| Train | journey_mode_train |
| Tramway | journey_mode_tramway |
| Walking | journey_mode_walking |

### Realtime

| Context | Resource name |
| --- | --- |
| Parking availability | journey_realtime_park |

### And more...

| Context | Resource name |
| --- | --- |
| Departure | journey_departure |
| Arrival | journey_arrival |
| My position | journey_my_position |
| Address | journey_address |
| POI | journey_poi |
| Stop area | journey_stop_area |
| Ridesharing pin | journey_ridesharing_pin |