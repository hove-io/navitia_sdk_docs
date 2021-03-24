---
layout: main
title: Getting started
parent: Expert iOS
grand_parent: Expert
nav_order: 1
permalink: /expert/ios/getting-started
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

The access to `Expert` module requires valid credentials to our private artifactory. Add the following line to your `.netrc` file and replace `USERNAME` and `PASSWORD` with your credentials:

```
machine kisiodigital.jfrog.io login USERNAME password PASSWORD
```
 
In your project, add the following lines to your `Podfile`:

```ruby
platform :ios, '10.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CanalTP/Podspecs.git' # Expert podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'ExpertSDK', '~> 0.2.0' # Expert Pod definition
end
```

## 🚀  Launching

You can now call any endpoint from `navitiaSdk` and its variety of builders that will help you request Navitia. As an example:

```swift
navitiaSDK.physicalModesApi.newCoverageRegionPhysicalModesRequestBuilder()
    .withRegion("YOUR_COVERAGE")
    .get { (result, error) in
        if let result = result {
            // Use result
        } else {
            // There was an error
        }
    }
```