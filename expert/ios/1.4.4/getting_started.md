---
layout: default
title: Getting started
parent: Expert iOS
grand_parent: Expert
nav_order: 1
permalink: /expert/ios/getting-started
---

# Getting Started

---

## Installation
Ajouter dans le fichier `~/.netrc`. Remplacer `USERNAME` et `PASSWORD` par les valeurs correspondantes :
```ruby
machine kisiodigital.jfrog.io login USERNAME password PASSWORD
```
 
Ajouter dans le fichier Podfile :
```ruby
source 'https://github.com/CanalTP/Podspecs.git'
```

et dans la section target :
```ruby
pod ‘NavitiaSDK’, ‘1.4.4’
```

Exécuter la commande :
```ruby
pod deintegrate && pod install
```


NavitiaSDKUX is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "NavitiaSDK"
```

## Configuration & initialization
```swift
let navitiaSDK = NavitiaSDK(configuration: NavitiaConfiguration(token: "my-token")
navitiaSDK.journeysApi.newJourneyRequestBuilder()
    .withFrom("2.38;48.84")
    .withTo("2.29;48.82")
    .get { (result, error) in
        if result != nil {
            let journeys = result!.journeys
        }
    }
```
