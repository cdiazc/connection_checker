# ConnectionChecker

[![Release](https://jitpack.io/v/muddassir235/connection_checker.svg?style=flat-square)](https://jitpack.io/#muddassir235/connection_checker/)

Android library for checking the internet connectivity of a device.

Used in https://play.google.com/store/apps/details?id=com.muddassirkhan.quran_android

## Add Dependencies
Add the following in your project level build.gradle
```groovy
allprojects {
    repositories {
        maven { url 'https://jitpack.io' }
    }
}
```
and the following in your app level build.gradle
```groovy
dependencies {
    implementation 'com.github.muddassir235:connection_checker:1.6'
}
```

## Use The Library

Instantiate an object
```kotlin
val connectionChecker = ConnectionChecker(this, lifecycle) 
```
By default it will ping https://www.google.com. The user can set the url to ping.
```kotlin
val connectionChecker = ConnectionChecker(this, lifecycle, "https://www.site.url") 
```

Add connectivity listener
```kotlin
connectionChecker.connectivityListener = object: ConnectivityListener {
    override fun onConnectionState(state: ConnectionState) {

    }
}
```

## Example
Example in an Android Activity.
```kotlin
class MainActivity : AppCompatActivity(), ConnectivityListener {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val connectionChecker = ConnectionChecker(this, lifecycle)
        connectionChecker.connectivityListener = this
    }

    override fun onConnectionState(state: ConnectionState) {
        connection_status_tv.text = if(state == ConnectionState.CONNECTED) {
            "Connected"
        } else if(state == ConnectionState.SLOW) {
            "Slow Internet Connection"
        } else {
            "Disconnected"
        }
    }
}
```

## Uses
* https://github.com/muddassir235/kmacros

## [Apps by Muddassir Ahmed](https://play.google.com/store/apps/developer?id=Muddassir+Khan):
* https://play.google.com/store/apps/details?id=com.muddassirkhan.quran_android
* https://play.google.com/store/apps/details?id=com.app.kitaabattawheed
