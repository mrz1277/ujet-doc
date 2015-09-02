#Initial setup on the web (for both of iOS and Android)
When a user schedules a call, UJET will send a notification to the mobile phone at the scheduled time. To enable the notification, you should open an API for notification and register your hosting app information. Please visit [setup page](http://staging.ujet.co/#/manager/company) and update the following information:
* API URL
* Oauth - app_id, secret_key, access_token
* Basic Auth, Digest Auth - username, password

#Setup for iOS
## Installation with CocoaPods
[CocoaPods](http://cocoapods.org) is a dependency manager for Objective-C, which automates and simplifies the process of using 3rd-party libraries like UJetSDK in your projects. See the ["Getting Started" guide for more information](https://guides.cocoapods.org/using/getting-started.html#getting-started).

### Podfile
```ruby
platform :ios, '7.0'
pod "UJetSDK", "~> 1.0"
```

## Setup
1. Add `#import "UJetSDK.h"` to `AppDelegate.m`

2. Add `[UJetSDK setup:appId withClientKey:clientKey withLaunchOptions:launchOptions]` to `- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions`
````objective-c
[UJetSDK setup:appId withClientKey:clientKey withLaunchOptions:launchOptions];
````

3. Add `[UJetSDK notification:userInfo]` to `- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo`
````objective-c
[UJetSDK notification:userInfo];
````

4. Add `#import "UJetSDK.h"` and execute `[UjetSDK show:deviceToken]` when you want to show UJET UI.
````objective-c
[UJetSDK showPopup: userIdentifier     // required  
         withName: name                // required 
         withPhone: phone              // optional 
         withAddress: address          // optional
         withDeviceToken: deviceToken  // optional
];
````

# Setup for Android

## Installation via Gradle

### build.gradle

```
dependencies {
    compile 'co.ujet.android:ujet:1.0.0'
}
```

## Installation via jar

Import .jar file under your library directory.

### Setup

1. Add permissions under `<manifest> in `AndroidManifest.xml`
```
<manifest>
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="com.samsung.android.providers.context.permission.WRITE_USE_APP_FEATURE_SURVEY" />
</manifest>
```

2. Add services under `<application>` in `AndroidManifest.xml`
```
<application>
    <service android:name="co.ujet.android.UjetClientService"
        android:exported="false"
        android:stopWithTask="false" />
</application>
```

3. Call initialize method on activity
```
Ujet.initialize(this, "APPLICATION ID", "CLIENT KEY");
Ujet.showDialog("APP NAME");
```
