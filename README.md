# my_inappwebview

The basic Flutter project template of Android Studio doesn't recognize CocoaPods when the plugin `flutter_inappwebview` is added in `pubspec.yaml`. 

But the same basic Flutter project works, when I replace its `main.dart` with [the code given as example in the `pub.dev` page](https://inappwebview.dev/docs/in-app-webview/basic-usage/).
You can verify using the code in following repo: [https://github.com/kvutien/test_in_app_webview](https://github.com/kvutien/test_in_app_webview)

Why?

## How to reproduce the bug
Pre-requisites: my `flutter doctor` shows something like this about its configuration.
```
Doctor summary (to see all details, run flutter doctor -v):
[✓] Flutter (Channel stable, 2.8.1, on macOS 12.1 21C52 darwin-arm, locale en-LU)
[✓] Android toolchain - develop for Android devices (Android SDK version 32.0.0)
[✓] Xcode - develop for iOS and macOS (Xcode 13.1)
[✓] Chrome - develop for the web
[✓] Android Studio (version 2021.1)
[✓] Connected device (2 available)

• No issues found!
```

Actions to reproduce the bug
- Clone on your local computer this repository. It is exactly the code generated by Android Studio when you create a `New Flutter Project`. I only added in `pubspec.yaml` the dependency `flutter_inappwebview`. 
- Open the project in Android Studio
- Select any iOS virtual device
- Run `pub get` to retrieve the dependencies
- Run the project

You should see the following error:
```
Launching lib/main.dart on iPad mini (6th generation) in debug mode...
Warning: CocoaPods not installed. Skipping pod install.
  CocoaPods is used to retrieve the iOS and macOS platform side's plugin code that responds to your plugin usage on the Dart side.
  Without CocoaPods, plugins will not work on iOS or macOS.
  For more info, see https://flutter.dev/platform-plugins
To install see https://guides.cocoapods.org/using/getting-started.html#installation for instructions.

CocoaPods not installed or not in valid state.
Error launching application on iPad mini (6th generation).
```

If you can't reproduce the error, maybe it is specific to Android Studio version ARM64? I have a Macbook Pro with the M1Pro chip.

## How to remove the error - method 1
- In Terminal `cd` to the project folder
- Type `flutter run` 

The build should work. Maybe the bug is specific to Android Studio?

## How to remove the error - method 2
- In `pubspec.yaml` comment out the following dependency by prefixing it with '# '
```
  flutter_inappwebview: ^5.3.2
```
- Run again `pub get` to update the dependencies
- Run the project in Android Studio

This time the build should work and you'll see the classical Flutter template app.