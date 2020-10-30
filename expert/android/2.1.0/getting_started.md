---
layout: default
title: Getting started
parent: Expert Android
grand_parent: Expert
nav_order: 1
permalink: /expert/android/getting-started
---

# Getting Started

---

## Installation
Add the following maven repository in the `build.gradle` of your project. Replace `USERNAME` and `PASSWORD` with your credentials
```ruby
repositories {
    ...
    maven {
        credentials {
            username = USERNAME
            password = PASSWORD
        }
        url("https://kisiodigital.jfrog.io/kisiodigital/android-release")
    }
}
```

Add the following dependency in the `build.gradle` file of your application
```ruby
dependencies {
    ...
    implementation("com.kisio.navitia.sdk.data:expert:2.1.0")
}
```

## Configuration & initialization
```java
NavitiaSDK sdk = new NavitiaSDK(new NavitiaConfiguration("my-token"));
sdk.journeysApi.newJourneysRequestBuilder()
    .withFrom("2.38;48.84")
    .withTo("2.29;48.82")
    .get(new ApiCallback<Journeys>() {
        @Override
        public void onFailure(ApiException e, int statusCode, Map<String, List<String>> responseHeaders) {
            
        }
        @Override
        public void onSuccess(Journeys result, int statusCode, Map<String, List<String>> responseHeaders) {
            List<Journey> journeys = result.getJourneys();
        }
        @Override
        public void onUploadProgress(long bytesWritten, long contentLength, boolean done) {

        }
        @Override
        public void onDownloadProgress(long bytesRead, long contentLength, boolean done) {

        }
    });
```