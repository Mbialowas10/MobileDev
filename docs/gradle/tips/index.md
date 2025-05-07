---
title: Tips and Tricks when working with Gradle
layout: home
nav_order: 1
parent: Gradle and Android Gradle Plugin (AGP)
has_children: false
---

## Tips and Tricks when working with Gradle

### Errors

```plaintext
1. e: Wrong plugin option format: null, should be plugin:<pluginId>:<optionName>=<value>
```

This error may present itself when reviewing someone else's code and is the result of *corrupted gradle caches*
somewhere in Android Studio.

To fix try the steps outlined below:

```plaintext
// Stop all gradle deamons
./gradlew --stop 

// Delete global cache dir
rm -R ~/.gradle 

// Clean working dir (if using git)
git clean -xfd

// Then do a full rebuild
./gradlew assemble
```
credits: *https://github.com/realm/realm-java/issues/5508*