# Running on Mobile

Meteor-made web apps are born **mobile-ready**, leveraging concepts like responsive design to adapt the user experience for diverse device capabilities. However, by default, these apps must run in a browser (desktop or mobile) and are faced with all the tradeoffs present in that environment.

By comparison, a **native mobile app** runs as an independent application on the mobile device, and can be packaged, and distributed, through the corresponding app stores for that mobile platform (e.g., iTunes for iOS, Google Play for Android etc.)

In general, each mobile device platform has its own SDK (Android, iOS, Windows Mobile), requiring the developer to maintain different codebases (and possibly versions of each codebase) to support the many targeted devices. This can be complex and costly. However, the benefits of app store distribution, access to specialized device hardware/APIs, offline operation, brandind etc. can make native applications attractive, if not mandatory, in some cases.

Because each mobile device OS is different, this typically requires the developer to maintain a different codebase for each target, which can be complex and costly. However, the benefits of app store listing, access to specialized device hardware/APIs, offline usage, branding etc. making native applications attractive.

Platforms like [Apache Cordova](http://cordova.apache.org/) are making this easier by exposing diverse device APIs in a consistent manner to a JavaScript client, allowing 'native' applications to be created using web technologies. Cordova takes this one step further, providing tools to package that application (as a native app) and deploy it to the appropriate application store.

As of Meteor 1.0, Apache Cordova support is now an integrated features, allowing developers to build native iOS or Android versions of their web apps in just a few commands.

**1. ANDROID
**

First install the SDK. It's a large *one-time* download and install. The download is fairly large and can take non-trivial time to complete.
```
meteor install-sdk android
```
If an sdk was installed previously, you will instead see something like this:
```
meteor install-sdk android
✓ Found Android bundle
✓ A JDK is installed
✓ Found Android Platform tools
✓ Found Android Build Tools
✓ Found Android 19 API
✓ Found suitable Android x86 image
✓ 'meteor' android virtual device (AVD) found
✓ Android emulator acceleration is installed
```


Next, add the android platform to the meteor project where you propose to build your mobile app.
```
meteor add-platform android
```
You will be required to accept the *Android SDK License Agreement* to proceed. This needs to be done on a per-application basis (rather than a one-time meteor installation basis).


**2. Running on an Android Device
**
```

```

**3. Running on an iOS Emulator
**
```

```

**4. Running on an iOS Device
**
```

```

# Notes

1) **:**

