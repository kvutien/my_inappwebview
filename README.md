# my_inappwebview

The basic Flutter project template of Android Studio with the plugin `flutter_inappwebview`

## How to reproduce the bug
Pre-requisites: your `flutter doctor` shows something like this
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
- Clone on your local computer this repository.
- Open the project in Android Studio
- Choose any iOS virtual device
- Run 'pub get' to retrieve the dependencies
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

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://flutter.dev/docs/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://flutter.dev/docs/cookbook)

For help getting started with Flutter, view our
[online documentation](https://flutter.dev/docs), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

## How to remove the error
- ,In `pubspec.yaml` comment out the following dependency by prefixing it with '# '
```
  flutter_inappwebview: ^5.3.2
```
- Run again 'pub get' to update the dependencies
- Run the project

This time the build should work and you'll see the classical Flutter template app.