#Expert iOS

## 💻  Setup

In your project, add the following lines to your `Podfile`:

```ruby
platform :ios, '10.0' # Minimum deployment target
use_frameworks!

source 'https://github.com/CanalTP/Podspecs.git' # Expert podspec URL

target 'YOUR_PROJECT_SCHEME' do
  pod 'ExpertSDK', '2.3.4' # Expert Pod definition
end
```

Using your CLI, run `pod install` in your project directory.

## 👨‍💻  Implementation

This module is set up by calling `Expert.shared.initialize()`.<br>

This method takes the following parameters:

| Parameter | Type | Required | Description | Default |
| --- | :---: | :---: | --- | :---: |
| `token` | `String` | ✓ | Navitia API access token | ✗ |
| `env` | `ExpertEnvironment` | ✗ | Navitia API environment | `ExpertEnvironment.prod` |
| `debugEnabled` | `Bool` | ✗ | Log Navitia responses | `false` |

```swift
Expert.shared.initialize(token: token,
                         environment: .prod,
                         debugEnabled: true)
```

* [Available APIs](apis.md)
* [Available models](models.md)

## 🚀  Launching

You can now call any endpoint from `Expert.shared` and its variety of functions with a completion block that will help you request Navitia. As an example:

```swift
Expert.shared.physicalModesApi.getCoverageRegionPhysicalModes(region: "YOUR_COVERAGE")  { result, rawData, error in
    if let error = error {
        // There was an error
    } else {
        // Use result Data or Raw Data
    }
}
```