cordova-android-firebase-gradle-release [![Latest Stable Version](https://img.shields.io/npm/v/cordova-android-firebase-gradle-release.svg)](https://www.npmjs.com/package/cordova-android-firebase-gradle-release) [![Total Downloads](https://img.shields.io/npm/dt/cordova-android-firebase-gradle-release.svg)](https://npm-stat.com/charts.html?package=cordova-android-firebase-gradle-release)
=======================================

This Cordova/Phonegap plugin for Android aligns versions of the Firebase library specified by other plugins to a specific version.

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

**TL;DR**: To prevent build failures caused by including different versions of the Firebase library.


To resolve these version collisions, this plugin injects a Gradle configuration file into the native Android platform project, which overrides any versions specified by other plugins, and forces them to the version specified in its Gradle file.

If you're encountering similar problems with the Android Support or Play Services libraries, checkout the sister plugins:
- [cordova-android-support-gradle-release](https://github.com/dpa99c/cordova-android-support-gradle-release).
- [cordova-android-play-services-gradle-release](https://github.com/dpa99c/cordova-android-play-services-gradle-release).

# Installation

    $ cordova plugin add cordova-android-firebase-gradle-release
    $ cordova plugin add cordova-android-firebase-gradle-release  --variable FIREBASE_VERSION={required version}
    
The plugin needs to be installed with the [`cordova-fetch`](https://cordova.apache.org/news/2016/05/24/tools-release.html) mechanism in order to satisfy its [package dependencies](https://github.com/dpa99c/cordova-android-firebase-gradle-release/blob/master/package.json#L8) by installing it via npm.

Therefore if you're installing with `cordova@6`, you'll need to explicitly specify the `--fetch` option:

    $ cordova plugin add cordova-android-firebase-gradle-release --fetch
    
# Library versions

## Default version
By default, this plugin will use the most recent major version the Firebase library:

    $ cordova plugin add cordova-android-firebase-gradle-release

## Other versions

In some cases, you may want to specify a different version of the Firebase library - [see here](https://firebase.google.com/support/release-notes/android) for a list recent versions.
So this plugin enables you to specify other versions of the Firebase library using the `FIREBASE_VERSION` plugin variable.
 
For example, if you want to install v12 of the Firebase library, you'd specify the version via the variable:

    cordova plugin add cordova-android-firebase-gradle-release --variable FIREBASE_VERSION=12.+

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