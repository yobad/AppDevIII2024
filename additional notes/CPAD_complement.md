---
layout: post
title: "Cross-Platform Native Apps - additional notes"
permalink: /lectures/cpad/additionalnotes
categories: notes



---

## Development process

- Cross-Platform App Development `CPAD`
- Use programming languages that are not native to the mobile OS. 
- The programming language itself is cross-platform.
- Includes multiple SDKs for the various platforms.

| <img src="../images/cpad/CPADprocess.png" /> |
| :------------------------------------------: |
|           *CPAD Building Process*            |

| <img src="../images/cpad/CPADTypes.png"/> |
| :---------------------------------------: |
|             *CPAD App Types*              |

### Drawbacks of using CPAD

- Performance
  - Even though CPAD frameworks claim to have a performance matching a native app, native apps tend to perform faster. 
  - Users will *NOT* notice the difference in most cases.
- App size
  - Native apps tend to have a smaller size after compilation.
  - Apps created using CPAD will be larger in size due to the fact that additional elements are added during the converting process.
- Constant Updating
  - When Google or Apple issue an update, an additional feature or a new API, CPAD frameworks must implement them and in a timely manner. 

## Popular Cross-platform Frameworks

<img src="../images/cpad/Cordova.png" width="50%" />

- Opensource `Hybrid` app development framework by Apache.
  - Single codebase that generates native Android and iOS apps.
- Languages used: 
  - JavaScript
  - UI: HTML5 & CSS3 for UI.
- Command line based: 
  - No IDE: web component built using the developer’s editor of choice. 
- Process:
  - Build web application. 
  - Cordova converts web app into native app. 
  - Cordova provides a large set of plugins to access native capabilities via JavaScript. 
- Excellent when a web app already exists and needs to be converted it into an app. 

---

<img src="../images/cpad/ReactNative.webp" width="50%" />

- Opensource `Cross-platform Native` app framework.
  - Single codebase that generates native Android and iOS apps.
- Based on Facebook's popular React JavaScript library. 
  - Created by Facebook because the performance of the hybrid mobile apps was not satisfactory. 
- Languages used: 
  - JavaScript & ECMAScript
  - UI: JSX & React Native components.
- Command line based. 
- React Native outputs a Native app that can be opened and extended in Android Studio or XCode.

---

<img src="../images/cpad/Flutter.webp" width="40%" />

- Opensource `Cross-platform Native` app framework by Google.
- Single codebase that generates:
  - Native Android and iOS apps.
  - Web Apps.
  - Desktop apps. 
- Languages used: 
  - Dart. (relatively new).
  - UI: Flutter Widgets.
- Integrates easily with Android Studio & Visual Studio.

---

<img src="../images/cpad/Ionic.png" width="35%" />

- Opensource `PWA` app framework.
- Single codebase that generates mobile apps.
- Languages used: 
  - Ract.
  - Angular.
  - Vue.
  - HTML5, CSS and JavaScript.
- Utilizes `Cordova` plugins that allow access to in-built device features such as Audio Recorder, GPS, and Camera..

---

<div style="text-align:center;">
    <img src="../images/maui_intro/maui.jpg" width="30%" class="inline-img"/>
    <img src="../images/cpad/apps.png" width="40%" class="inline-img" />
</div>


- `Cross-platform Native` app framework by Microsoft.
- .NET MAUI is the successor of Xamarin.Forms.
- Many changes brought to Xamarin.Forms.
- Will be discussed in more detail in this course.

---

## Other frameworks worth mentioning

<img src="../images/cpad/Solar2D.svg" width="35%" />

- Opensource Cross-platform.
- 2D Gaming engine.
- Singe codebase to create gaming apps for :
  - Mobile.
  - Desktop.
  - Connected TV devices.
- Uses `Lua` programming language.

---

<img src="../images/cpad/CodenameOne.png" width="35%" />

- Opensource Cross-Platform app framework. 
- For `Java` lovers.
- Single codebase to build:
  - Native apps for Android, iOS.
  - Desktop apps.
  - Web apps.
- Installs as a plugin in Eclipse, NetBeans, and IntelliJ.

---

### Sources

https://www.captechu.edu/blog/brief-history-of-mobile-apps
https://edu.gcfglobal.org/en/computerbasics/understanding-applications/1/
https://www.nationaldayarchives.com/day/national-app-day/
https://nationaltoday.com/national-app-day/
https://www.netsolutions.com/insights/cross-platform-app-frameworks-in-2019/#the-difference-between-native-and-cross-platform-app-development
https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps
https://flutter.dev/
https://reactnative.dev/
https://cordova.apache.org/
https://ionicframework.com/
https://solar2d.com/
https://www.codenameone.com/