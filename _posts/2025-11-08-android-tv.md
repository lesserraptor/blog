---
layout: post
title: "android tv mods"
tags: android
---
i did this a while ago, but i wanted to publish it here so i don't lose it.

if you have a smart tv that uses android tv, you can easily customize it to remove most of the visual bloat that a smart tv comes with. additionally, you can use an android app called "smarttube" to watch youtube instead of the native google client. smarttube blocks all youtube ads, and it also cuts out any in-video sponsored content if it's already been flagged as sponsored content. it's really great, especially if you have kids that you don't want exposed to ads all day long. (i mean, youtube is a bit of an ad all by itself, but they're already paying with their attention, they don't need to also pay with money)
    
**here's the steps to install flauncher:**
- if you prefer to read this on the flauncher site, go here: [https://gitlab.com/flauncher/flauncher](https://gitlab.com/flauncher/flauncher)
- install flauncher using google play. nothing fancy here.
- once you have it installed, you can disable the default launcher. this is a bit risky, but it can be undone. first, [install adb on your computer](https://www.xda-developers.com/install-adb-windows-macos-linux/).
- use adb to connect to the tv: <code>adb connect your.tv.ip.address</code>
- now, disable the google provided ad-machine launcher: <code>adb shell pm disable-user --user 0 com.google.android.apps.tv.launcherx</code>
- also, disable the fallback launcher: <code>$ adb shell pm disable-user --user 0 com.google.android.tungsten.setupwraith</code>
- note that this will probably kill some of the features of your remote, in particular the "voice commands" stuff. that stuff creeps me out, so i was ok with this loss of functionality.
    
    
**here's the steps to install smarttube:**
- make sure you have [adb installed on your computer](https://www.xda-developers.com/install-adb-windows-macos-linux/)
- download the latest smarttube release here: [https://github.com/yuliskov/SmartTube/releases](https://github.com/yuliskov/SmartTube/releases)
- use adb to connect to the tv: <code>adb connect your.tv.ip.address</code>
- you'll probably need to use the tv remote to "allow" your computer to connect to it. it's best to have a laptop in the same room as the tv so you can look at both screens at once.
- make sure you are in the directory that contains the smarttube file you already downloaded, and tell adb to install it: <code>adb install SmartTube_stable_22.44_armeabi-v7a.apk</code>
- give the smarttube app install rights so that it can update itself later: <code>adb shell appops set com.liskovsoft.smarttubetv.beta REQUEST_INSTALL_PACKAGES allow</code>
- later, if you can't remember that the smarttube package was called "com.liskovsoft.smarttubetv.beta", you can look it up with this command: <code>adb shell cmd package list packages | grep smart</code>
