<p align="center">
<a href="http://www.customerly.io">
<img src="https://www.cdn.customerly.io/assets/img/Logo_Customerly_Name_Colored.svg">
</p>

  [![Language](https://img.shields.io/badge/Swift-3-orange.svg)]()
  [![Language](https://img.shields.io/badge/Objective--C-compatible-blue.svg)]()
  [![License](https://img.shields.io/badge/license-Apache%20License%202.0-red.svg)]()
  
**customerly.io** is the perfect tool to getting closer to your customers. Help them where they are with the customer support widget. Manage your audience based on their behaviours, build campaigns and automations.

Deliver Surveys directly into your app and get the responses in one place. Study your Net Promote Score and Skyrocket your Online Business right now.

The Customerly iOS SDK is really simple to integrate in your apps, and allow your users to contact you via chat.

<p align="center">
  <img src="https://github.com/customerly/customerly.github.io/blob/master/ios/resources/chat-preview.png?raw=true" width=500 alt="Icon"/>
</p>

## Features

- [x] Register your users
- [x] Set attributes
- [x] Track events
- [x] Support via chat in real time
- [x] Surveys
- [x] English & Italian localizations
- [x] Objective-C compatibility
- [x] Many more is coming....

## Requirements

- iOS 8.0+
- Xcode 8+
- Swift 3 or Objective-C

## CocoaPods

To use the Customerly SDK we recommend to use Cocoapods 1.0.0 or later

[CocoaPods](http://cocoapods.org) is a dependency manager for Cocoa projects. You can install it with the following command:

```bash
$ gem install cocoapods
```

To integrate the Customerly SDK into your Xcode project using CocoaPods, specify it in your `Podfile`:


```ruby
source 'https://github.com/CocoaPods/Specs.git'
platform :ios, '8.0'
use_frameworks!

pod 'CustomerlySDK', :git => 'https://github.com/customerly/Customerly-iOS-SDK'
```

Then, run the following command:

```bash
$ pod install
```

## Usage
If you are setting up a new project, you need to install the SDK. You may have already completed this as part of creating a Customerly account. We recommend using CocoaPods 1.0.0 or later to install the SDK.

First of all, if you don't have an Xcode project yet, create one, then install the SDK following the paragraph `Cocoapods`.

**1)** Import the Customerly iOS SDK module in your UIApplicationDelegate subclass:

```
import CustomerlySDK
```
**2)** Configure a Customerly iOS SDK shared instance, in your App Delegate, inside **application:didFinishLaunchingWithOptions:** method:

```
Customerly.sharedInstance.configure(appId: "YOUR_CUSTOMERLY_APP_ID")
```
also add inside **applicationDidBecomeActive:**

```
Customerly.sharedInstance.activateApp()
```

If you want to enable the logging in console, you can set verboseLogging variable to true. By default verbose logging is disabled.

```
Customerly.sharedInstance.verboseLogging = true
```

**3)** From iOS 10, you'll need to make sure that you add `NSPhotoLibraryUsageDescription` & `NSCameraUsageDescription` to your Info.plist so that your users have the ability to upload photos in Customerly's chat. Furthermore remember to set the `NSAppTransportSecurity` to `NSAllowsArbitraryLoads`.

**If in doubt, you can look at the examples in the demo application.**


### User registration
You can register logged in users of your app into Customerly calling the method `registerUser:`. You’ll also need to register your user anywhere they log in.

Example:

```
Customerly.sharedInstance.registerUser(email: "axlrose@example.com", user_id: "123ABC", name: "Axl Rose")
```

or using a closure

```
Customerly.sharedInstance.registerUser(email: emailTextField.text!, user_id: userIdTextField.text, name: nameTextField.text, success: { 
                //Success
            }, failure: { 
                //Failure
            })
```

You can also logout users:

```
Customerly.sharedInstance.logoutUser()
```

In this method, *user_id*, *name*, *attributes*, *success* and *failure* are optionals.

If you don't have a login method inside your apps don't worry, users can use the chat using their emails.

###Chat
You can open the support view controller calling the method `openSupport:`

```
Customerly.sharedInstance.openSupport(from: self)
```
where **self** is your current view controller.

###Surveys (nothing to do)

With the Customerly SDK you can deliver surveys directly into your app app without any lines of code.

They will be automatically displayed to your user as soon as possible.

Remember that you can get updates about new surveys available using the `update:` method.

###Attributes
Inside attributes you can add every custom data you prefer to track.

```swift
// Eg. This attribute define what kind of pricing plan the user has purchased 
Customerly.sharedInstance.setAttributes(attributes: ["pricing_plan_type" : "basic"])
```

###Events
Send to Customerly every event you want to segment users better

```
// Eg. This send an event that track a potential purchase
Customerly.sharedInstance.trackEvent(event: "added_to_cart")
```

###Extra

If you want to get a generic update, call `update:`

```
Customerly.sharedInstance.update(success: { 
            //Update success
        }) { 
            //Update failure
        }

```

## Contributing

- If you **need help** or you'd like to **ask a general question**, open an issue or contact our support on [Customerly.io](https://www.customerly.io)
- If you **found a bug**, open an issue.
- If you **have a feature request**, open an issue.
- If you **want to contribute**, submit a pull request.


## Acknowledgements

Made with ❤️ by [Paolo Musolino](https://github.com/Codeido) for Customerly.


## License
Customerly iOS SDK is available under the Apache License 2.0. See the LICENSE file for more info.
