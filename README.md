cordova-android-firebase-gradle-release [![Latest Stable Version](https://img.shields.io/npm/v/cordova-android-firebase-gradle-release.svg)](https://www.npmjs.com/package/cordova-android-firebase-gradle-release) [![Total Downloads](https://img.shields.io/npm/dt/cordova-android-firebase-gradle-release.svg)](https://npm-stat.com/charts.html?package=cordova-android-firebase-gradle-release)
=======================================

Cordova/Phonegap plugin for Android to align versions of the Firebase library components specified by other plugins to a specific version.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [Purpose](#purpose)
- [Installation](#installation)
- [Library versions](#library-versions)
  - [Default version](#default-version)
  - [Other versions](#other-versions)
- [Credits](#credits)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->
 
# Purpose

**TL;DR**: To prevent build failures caused by Cordova plugins including different versions of Firebase library components.

To resolve these version collisions, this plugin injects a Gradle configuration file into the native Android platform project, which overrides any versions specified by other plugins, and forces them to the version specified in its Gradle file.

If you're encountering similar problems with the Android Support or Play Services libraries, checkout the sister plugins:
- [cordova-android-support-gradle-release](https://github.com/dpa99c/cordova-android-support-gradle-release).
- [cordova-android-play-services-gradle-release](https://github.com/dpa99c/cordova-android-play-services-gradle-release).

# Requirements

This plugin requires `cordova@8+` (CLI) and `cordova-android@7+` (Android platform).
Since the plugin uses hook scripts it will not work in Cloud Build environments such as Phonegap Build.

# Installation

    # override using default component versions
    $ cordova plugin add cordova-android-firebase-gradle-release
    
    ## override using custom component versions 
    $ cordova plugin add cordova-android-firebase-gradle-release  --variable firebase-core=17.0.0 --variable firebase-messaging=19.0.0
    
# Component versions
This plugin enables overriding the version of the following Firebase SDK library components:

	Firebase Core	com.google.firebase:firebase-core
	Ads	com.google.firebase:firebase-ads
	Analytics	com.google.firebase:firebase-analytics
	App Indexing	com.google.firebase:firebase-appindexing
	Authentication	com.google.firebase:firebase-auth
	Cloud Firestore	com.google.firebase:firebase-firestore
	Cloud Functions	com.google.firebase:firebase-functions
	Cloud Messaging	com.google.firebase:firebase-messaging
	Cloud Storage	com.google.firebase:firebase-storage
	Crash Reporting	com.google.firebase:firebase-crash
	Crashlytics	com.crashlytics.sdk.android:crashlytics
	Dynamic Links	com.google.firebase:firebase-dynamic-links
	Invites	com.google.firebase:firebase-invites
	In-App Messaging	com.google.firebase:firebase-inappmessaging
	In-App Messaging Display	com.google.firebase:firebase-inappmessaging-display
	ML Kit: Vision APIs	com.google.firebase:firebase-ml-vision
	ML Kit: Image Labeling Model	com.google.firebase:firebase-ml-vision-image-label-model
	ML Kit: Face Detection Model	com.google.firebase:firebase-ml-vision-face-model
	ML Kit: Object Detection and Tracking Model	com.google.firebase:firebase-ml-vision-object-detection-model
	ML Kit: Natural Language APIs	com.google.firebase:firebase-ml-natural-language
	ML Kit: Language Identification Model	com.google.firebase:firebase-ml-natural-language-language-id-model
	ML Kit: Translate Model	com.google.firebase:firebase-ml-natural-language-translate-model
	ML Kit: Smart Reply Model	com.google.firebase:firebase-ml-natural-language-smart-reply-model
	ML Kit: Custom Model APIs	com.google.firebase:firebase-ml-model-interpreter
	ML Kit: AutoML Vision Edge API	com.google.firebase:firebase-ml-vision-automl
	Performance Monitoring	com.google.firebase:firebase-perf
	Realtime Database	com.google.firebase:firebase-database
	Remote Config	com.google.firebase:firebase-config

## Default version
By default, this plugin pins a recent major version of each of the Firebase library components.
You can see what the currently pinned versions are by looking at the `<preference>`'s in the [`plugin.xml`](https://github.com/dpa99c/cordova-android-firebase-gradle-release/blob/master/plugin.xml).

## Other versions
You may want to specify a version the Firebase library components - [see here](https://firebase.google.com/support/release-notes/android) for a list recent versions.

Library component versions are specified in the Android build as Gradle artifacts in the format `packageId:componentId:versionNumber`, for example `com.google.firebase:firebase-core:17.0.0`.
To override the default version when installing this plugin, specify a plugin variable where then variable key is the component ID and the value is the version number. 
For example, if you want to install v17.0.0 of the Firebase Core library component, you'd specify the version via the variable:

    cordova plugin add cordova-android-firebase-gradle-release --variable firebase-core=17.0.0
    
You can also specify the the overrides directly in the `config.xml` and this plugin will find them, for example:

    <plugin name="cordova-android-firebase-gradle-release" spec="^4.0.0">
        <variable name="firebase-core" value="17.0.0" />
    </plugin>

Or in the `package.json`, e.g.:

    {
        "cordova": {
            "plugins": {
                "cordova-android-firebase-gradle-release": {
                    "firebase-core": "17.0.0"
                    }        
                }
            }
        }
    }           

Note: the plugin is case-insensitive to the component ID so `firebase-core` or `FIREBASE-CORE` will both work.    

# Credits

Thanks to [**Chris Scott, Transistor Software**](https://github.com/christocracy) for his idea of extending the initial implementation to support dynamic specification of the library version via a plugin variable in [cordova-google-api-version](https://github.com/transistorsoft/cordova-google-api-version)


License
================

The MIT License

Copyright (c) 2018 Dave Alden / Working Edge Ltd.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
