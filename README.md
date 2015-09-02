#Setup on web
When a user schedules call, UJET will send a notification to the mobile phone at the scheduled time. To send notification, you should open API for notification and register information their information. Please visit [setup page](http://staging.ujet.co/#/manager/company) and update this information
* API URL
* app_id, secret_key, access_token(oauth) or username, password(basic, digest)

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

2. Add `[UJetSDK setup:applicationKey withLaunchOptions:launchOptions]` to `- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions`
````objective-c
[UJetSDK setup:applicationKey withLaunchOptions:launchOptions];
````

3. Add `[UJetSDK setup:applicationKey withLaunchOptions:launchOptions]` to `- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo`
````objective-c
[UJetSDK notification:userInfo];
````

4. Add `#import "UJetSDK.h"` and execute `[UjetSDK show:deviceToken]` when you want to show UJET popup.
````objective-c
[UJetSDK showPopup:email withDeviceToken:deviceToken];
````
