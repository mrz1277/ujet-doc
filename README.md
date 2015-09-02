#Initial setup on the web (for both of iOS and Android)
When a user schedules a call, UJET will send a notification to the mobile phone at the scheduled time. To enable the notification, you should open an API for notification and register your hosting app information. Please visit [setup page](http://staging.ujet.co/#/manager/company) and update the following information:
* API URL
* Oauth - app_id, secret_key, access_token(oauth)
or
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

2. Add `[UJetSDK setup:applicationKey withLaunchOptions:launchOptions]` to `- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions`
````objective-c
[UJetSDK setup:applicationKey withLaunchOptions:launchOptions];
````

3. Add `[UJetSDK setup:applicationKey withLaunchOptions:launchOptions]` to `- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)userInfo`
````objective-c
[UJetSDK notification:userInfo];
````

4. Add `#import "UJetSDK.h"` and execute `[UjetSDK show:deviceToken]` when you want to show UJET UI.
````objective-c
[UJetSDK showPopup:userId             // required  
         withName:name                // required 
         withPhone:phone              // optional 
         withAddress:address          // optional
         withDeviceToken:deviceToken  // optional
];
````
