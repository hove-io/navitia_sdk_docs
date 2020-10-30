---
layout: default
title: Getting started
parent: Journey iOS
grand_parent: Journey
nav_order: 1
permalink: /journey/ios/getting-started
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
pod ‘NavitiaSDKUI’, ‘3.4.5’
```
 
Exécuter la commande :
```ruby
pod deintegrate && pod install
```


NavitiaSDKUX is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "NavitiaSDKUI"
```

## Configuration & initialization