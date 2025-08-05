# Prompt 

The prompt that generated the provided setup guide was:

"Give me a comprehensive guide for setting up Flutter development targeting both the oldest and newest Android versions possible, for both Android Studio and Visual Studio Code (VSCode). Assume that I will be using my phone as a WiFi-based emulator for testing."

# Universal Flutter Development Setup (2025): Android Studio & VSCode

This guide will help you set up Flutter for **both Android Studio and Visual Studio Code (VSCode)**, ensuring your apps work on the **oldest (API 21, Android 5.0 Lollipop)** and **newest (API 35, Android 15)** Android versions available in August 2025. It assumes you will use your **phone as a WiFi-based emulator** (i.e., wireless debugging).

## 1. Install Essential Tools

### Android Studio
- Download the latest from the official Android Studio website.
- Complete installation using the standard process[1][2].

### Visual Studio Code (VSCode)
- Download from the official VSCode website and install.
- Recommended: Install the stable version[3].

## 2. Install Flutter SDK

- Download the latest Flutter SDK from the official site.
- Extract and **add `flutter/bin` to your system `PATH`**.
- Run in the terminal:
  ```bash
  flutter doctor
  ```
- Follow instructions to complete dependencies for Android (install Android SDK if prompted)[1][3][4].

## 3. Install Dart & Flutter Extensions/Plugins

### In Android Studio:
- Open **File > Settings > Plugins** (or **Preferences** on macOS).
- Search for **Flutter**, install and accept to add **Dart** as well.
- Restart Android Studio[1][5][6][7].

### In VSCode:
- Go to **Extensions** (`Ctrl+Shift+X`).
- Search for and install the **Flutter** extension (this will also install Dart).

## 4. Android SDK & Project Configuration

### Set Compatibility for Oldest and Newest Android Versions

- Open or create a Flutter project.
- In `android/app/build.gradle`, set:
  ```groovy
  android {
      defaultConfig {
          minSdkVersion 21        // Lollipop 5.0
          targetSdkVersion 35     // Android 15
      }
      compileSdkVersion 35       // Android 15
  }
  ```


- In **Android Studio**, use the **SDK Manager** to ensure:
  - Android SDK Platform 21 (for Lollipop)
  - Android SDK Platform 35 (latest)
  - Platform Tools, Build-Tools, Command-line Tools are all installed[3][4].

## 5. Use Your Phone as a WiFi Emulator (Wireless Debugging)

You can debug directly on your phone wirelessly instead of an emulator.

### 1. Phone Preparation
- Enable **Developer Options** on your phone.
- Turn on **USB Debugging** and **Wireless Debugging**.

### 2. Connect via WiFi
- Connect the phone and your PC to the same WiFi network.
- **First Time Only:** Connect via USB and authorize your PC.
- In your terminal, run:
  ```bash
  adb tcpip 5555
  adb connect [your.phone.ip.address]:5555
  adb devices  # Should now show your device as connected
  ```
  Replace `[your.phone.ip.address]` with your phone’s actual address.

### 3. Use in VSCode & Android Studio
- Both editors will auto-detect the connected device when running `flutter run`, using **Device Selector/Manager** or directly in the terminal[3][6].

## 6. Testing Range of Android APIs

- Always test on your physical device (current Android version).
- You can also set up additional emulator images for API 21 and API 35 in Android Studio if desired.
- Testing on a real, modern device ensures compatibility with the latest OS.

## 7. Key Commands

- Check environment:
  ```bash
  flutter doctor
  flutter devices
  flutter run
  ```
- Run on a specific device if you have multiples:
  ```bash
  flutter run -d [device_id]
  ```

## 8. Quick Recap Table

| Tool            | Required Steps                                                   |
|-----------------|-----------------------------------------------------------------|
| Android Studio  | Install → Flutter + Dart plugins → SDKs (21 & 35) → Set Gradle  |
| VSCode          | Install → Flutter extension → Set Gradle → Use terminal         |
| Phone Setup     | Enable Developer + Wireless Debugging → ADB connect             |
| Supported APIs  | 21 (Lollipop, min) to 35 (Android 15, current max)              |
| Run & Test      | Use `flutter run` or editor UI; test across versions            |

## Conclusion

This setup lets you code with **either (or both) Android Studio and VSCode**, target the full range of Android devices supported by Flutter in 2025, and efficiently use your real phone for wireless development and testing. Update your tools regularly and always check for plugin compatibility for lowest APIs.

You’re now ready for universal, cross-editor Flutter development![1][3][8][4][9]

[1] https://docs.flutter.dev/tools/android-studio
[2] https://developer.android.com/studio
[3] https://docs.flutter.dev/get-started/install/windows/mobile
[4] https://docs.flutter.dev/platform-integration/android/setup
[5] https://www.geeksforgeeks.org/android/android-studio-setup-for-flutter-development/
[6] https://www.youtube.com/watch?v=jftxz4SOEqI
[7] https://www.codecademy.com/article/installing-android-studio-on-windows-for-flutter
[8] https://docs.flutter.dev/release/breaking-changes/android-kitkat-deprecation
[9] https://docs.flutter.dev/reference/supported-platforms
