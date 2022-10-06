# Expert Android

## 💻 Setup

Add the following dependency in the `build.gradle` file of your application:

``` groovy
dependencies {
    implementation("com.kisio.navitia.sdk.data:expert:3.2.1")
}
```

## 👨‍💻 Implementation

This module is set up by simply instanciate 2 objects: 
- `NavitiaConfiguration` will hold your Navitia token
- `NavitiaSDK` will hold `NavitiaConfiguration`

``` kotlin
val navitiaSdk = NavitiaSDK(NavitiaConfiguration(token))
```

* [Available APIs](apis.md)
* [Available models](models.md)

## 🚀 Launching

You can now call any endpoint from `navitiaSdk` and its variety of builders that will help you request Navitia. As an example:

``` kotlin
navitiaSdk.physicalModesApi.newCoverageRegionPhysicalModesRequestBuilder()
    .withRegion("YOUR_COVERAGE")
    .get(object : ApiCallback<T> {
        override fun onSuccess(
            result: T,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Success result
        }

        override fun onFailure(
            e: ApiException?,
            statusCode: Int,
            responseHeaders: MutableMap<String, MutableList<String>>?
        ) {
            // Failure result
        }

        override fun onUploadProgress(bytesWritten: Long, contentLength: Long, done: Boolean) {
            // Progress upload
        }

        override fun onDownloadProgress(bytesRead: Long, contentLength: Long, done: Boolean) {
            // Progress download
        }
    })
```

You can use this folliwing utility function to benefit from the advantages of coroutines

``` kotlin
@InternalCoroutinesApi
@ExperimentalCoroutinesApi
private suspend fun <T> awaitApiCallback(block: (ApiCallback<T>) -> Unit): Result<T> =
    suspendCancellableCoroutine { cont ->
        block(object : ApiCallback<T> {

            override fun onSuccess(
                result: T,
                statusCode: Int,
                responseHeaders: MutableMap<String, MutableList<String>>?
            ) {
                cont.resume(Result.success(result)) {}
            }

            override fun onFailure(
                e: ApiException?,
                statusCode: Int,
                responseHeaders: MutableMap<String, MutableList<String>>?
            ) {
                cont.resume(Result.failure<ApiException>(e as ApiException)) {}
            }

            override fun onUploadProgress(bytesWritten: Long, contentLength: Long, done: Boolean) {
            }

            override fun onDownloadProgress(bytesRead: Long, contentLength: Long, done: Boolean) {
            }
        })
    }
```
and use it like so

``` kotlin
val result = awaitApiCallback<PhysicalModes> {
    navitiaSDK.physicalModesApi.newCoverageRegionPhysicalModesRequestBuilder()
        .withRegion("YOUR_COVERAGE")
        .get(it)
}
```
