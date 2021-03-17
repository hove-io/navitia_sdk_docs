---
layout: main
title: Getting started
parent: Journey iOS
grand_parent: Journey
nav_order: 1
permalink: /journey/ios/getting-started
---

# Getting Started
{: .no_toc }

---

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 🧰  Requirements

- [Cocoapods](https://cocoapods.org): this module is available through Cocoapods.
- Minimum iOS deployment target: 10.0

## 💻  Setup

The access to `Journey` module and its dependencies requires valid credentials to our private artifactory. Add the following line to your `.netrc` file and replace `USERNAME` and `PASSWORD` with your credentials:

```
machine kisiodigital.jfrog.io login USERNAME password PASSWORD
```
 
In your project, add the following lines to your `Podfile`:

```ruby
platform :ios, '10.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CanalTP/Podspecs.git' # Journey podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'NavitiaSDKUI', '~> 3.4.5' # Journey Pod definition
end
```

## 👨‍💻 Implementation

<div markdown="1">

</div>

#### Example
```swift
JourneySdk.shared.applicationBundle = Bundle.main
JourneySdk.shared.formJourney = false
JourneySdk.shared.advancedSearchMode = false
JourneySdk.shared.maxHistory = 12
JourneySdk.shared.isEarlierLaterFeatureEnabled = true
JourneySdk.shared.multiNetwork = true
```

## 🛠 Configuration

<div markdown="1">

| Configuration | Required | Description |
| --- |:---:| --- |
| `` | ✓ | To set the main color |
| `.primary` | ✗ | To set the secondary color |
| `.origin`  | ✗ | To set the color of the origin icon on the map and the roadmap departure block |
| `.originBackground`  | ✗ | To set the color of the roadmap departure block |
| `.originIcon`  | ✗ | To set the color of the origin icon on a departure search field and on the map  |
| `.destination` | ✗ | To set the color of the destination icon on the map and the roadmap arrival block |
| `.destinationBackground`  | ✗ | To set the color of the roadmap arrival block  |
| `.destinationIcon`  | ✗ | To set the color of the destination icon on a arrival search field and on the map |

</div>

## 🚀 Launching

### Journeys request
{: .no_toc }

### Transport Mode
{: .no_toc }

- Some use cases
{: .no_toc }

### Launching views

This module needs to be initialized before launching the main `ViewController`. Therefore, You need to call the `Journey.shared.initialize()` method.\

#### Launching with Form
{: .no_toc }

```swift
do {

} catch {
    Logger.error("%@", String(format: "JourneySDK cannot be initialized! %@", error.localizedDescription))
}
```

#### Launching with Journeys
{: .no_toc }

```swift
do {

} catch {
    Logger.error("%@", String(format: "JourneySDK cannot be initialized! %@", error.localizedDescription))
}
```
