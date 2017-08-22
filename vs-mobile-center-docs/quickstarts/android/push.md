---
# required metadata

title: Send Push Notifications to Users | Android Sample App Tutorials
description: Tutorial to send a push notification to the sample Android app.
keywords: mobile-center
authors: sshibu
ms.author: t-shshib
ms.date: 07/26/2017
---


# Send Push Notifications to Users
First, follow the [getting started tutorial](getting-started.md) to set up the sample app.

### Prerequisites
 - Signed APK.
 - Distributed sample app to your device (not running on emulator).
 - Google account.

## Integrate Mobile Center SDK
*The following directions are also located in the push service on Mobile Center.*
1. Locate the following in **app/build.gradle** and add the compile statement:

``` java
dependencies {  
      def mobileCenterSdkVersion = ' 0.11.0'
      compile "com.microsoft.azure.mobile:mobile-center-push:${mobileCenterSdkVersion}"
}
```

2. Locate the Mobile Center import statement in **MainActivity.java** and add the push import statement below it:

```java
import com.microsoft.azure.mobile.MobileCenter;
import com.microsoft.azure.mobile.push.Push;
```

3. Locate **onCreate** and add `Push.class` to `MobileCenter.start`:

```java
MobileCenter.start(getApplication(), "<APP SECRET HERE>",
         Analytics.class, Crashes.class, Push.class);
```

## Use Firebase Assistant to set up Firebase Cloud Messaging
1. Navigate to the app in Android Studio.
2. Go to the Firebase Assistant from the tool bar by clicking on **Tools > Firebase**.
3. Click on Cloud Messaging and click on **Set up Firebase Cloud Messaging**.
4. Connect your app to Firebase.
5. Add Firebase Cloud Messaging to your app. Ignore all other steps in the Firebase Assistant.
6. The Mobile Center SDK manages the following for you; if added automatically, please remove to avoid errors:

```java
  compile "com.google.firebase:firebase-core:${version}"
  compile "com.google.firebase:firebase-messaging:${version}"
```


## Set up Push in Mobile Center
1. Go to the **Push** service in [Mobile Center](https://mobile.azure.com/apps).
2. Click **Next** twice and skip the first and second pages.
3. Go to the [Firebase Console](https://console.firebase.google.com/) and select the project.
4. Navigate to Project Settings and copy your server key.
5. Paste your server key in Mobile Center.
  ![Obtain Server Key](images/serverKey.gif)

## Set up a push notification
1. Follow the [Distribute tutorial](distribute.md) to download the app to your device.
2. Navigate to the **Push** service in Mobile Center.
3. Click **Send notification**.
4. Set the **Campaign Name** as "Using Push Notifications". Set the **Message** as "Testing".  

## Send a push notification
1. Click **Next** at the bottom.
2. Choose **All registered devices**.
3. Click **Next** and **Send notification** at the bottom.

> [!NOTE]
> A push notification will be sent to the device you
> distributed to. It will not show up in the simulator.