# Expert Android

## 💻 Setup

Add the following dependency in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.data:expert:3.4.1")
}
```

## 👨‍💻 Implementation

This module is set up by calling `ExpertSdk.getInstance()`. The singleton behaves like a builder in which each method allows you to configure the module. Then, you need to call the `init()` method at the end. You should call this method in an `Application` subclass.<br>
This method takes the following parameters:

| Name | Required | Description | Type | Default |
| --- |:---:| --- | :---: | :---: |
| `token` | :material-check: | <a href="https://navitia.io/inscription/" target="_blank">Get your token</a> | `String` | :material-close: |
| `env` | :material-check: | Environment in which the module is launched | `NavitiaEnvironment` | :material-close: |

<h4>Example</h4>

``` kotlin
val expertSdk = ExpertSdk.getInstance().apply {
    init(
        token = "your_token",
        env = NavitiaEnvironment.PROD
    )
}
```

* [Available APIs](apis.md)
* [Available models](models.md)

## 🚀 Launching

You can now call any endpoint from `expertSdk` and its variety of builders that will help you request Navitia. As an example:

``` kotlin
try {
    val request = expertSdk.physicalModesApi.getCoverageRegionPhysicalModes(
        region = "your_coverage"
    )
    if (request.isSuccessful) {
        val result = request.body() as PhysicalModes
        // Handle result
    } else {
        // Handle failure
    }
} catch (ex: Exception) {
    // Handle failure exception
}   
```
