# Google Maps API Key Setup Guide

This guide explains how to securely add your Google Maps API key to the favorite_places project.

## Overview

The Google Maps API key is configured securely using:
- **Android**: Secrets Gradle Plugin with `local.properties`
- **iOS**: Xcode build configuration file (`GoogleService.xcconfig`)

Both methods prevent accidental exposure of your API key in version control.

## Prerequisites

1. A Google Maps API key from [Google Cloud Console](https://console.cloud.google.com/)
2. Enable the following APIs:
   - Maps SDK for Android
   - Maps SDK for iOS
   - Google Places API (optional)
   - Geocoding API (optional)

## Android Setup

### Step 1: Add Your API Key to local.properties

Edit `android/local.properties` and add your Google Maps API key:

```properties
sdk.dir=/Users/eslam/Library/Android/sdk
flutter.sdk=/Users/eslam/Flutter/SDK
MAPS_API_KEY=YOUR_ACTUAL_GOOGLE_MAPS_API_KEY
```

**Important**: Replace `YOUR_ACTUAL_GOOGLE_MAPS_API_KEY` with your actual API key.

### How It Works

The Secrets Gradle Plugin automatically reads the `MAPS_API_KEY` from `local.properties` and:
1. Injects it as a build configuration variable
2. Makes it available in `AndroidManifest.xml` via `${MAPS_API_KEY}`
3. Registers it with Google Maps at runtime

The `local.properties` file is already listed in `.gitignore`, so your API key won't be committed to version control.

## iOS Setup

### Step 1: Create GoogleService.xcconfig

A template file has been created at `ios/Runner/GoogleService.xcconfig`. Edit it and add your API key:

```
// This file contains sensitive information - do not commit to version control
GOOGLE_MAPS_API_KEY = YOUR_ACTUAL_GOOGLE_MAPS_API_KEY
```

**Important**: Replace `YOUR_ACTUAL_GOOGLE_MAPS_API_KEY` with your actual API key.

### Step 2: Configure Info.plist

Add the Google Maps API key to `ios/Runner/Info.plist`:

```xml
<!-- Find the <dict> tags and add this inside: -->
<key>GoogleMapsAPIKey</key>
<string>$(GOOGLE_MAPS_API_KEY)</string>
```

Or use Xcode:
1. Open `ios/Runner.xcworkspace` in Xcode
2. Select the Runner project
3. Go to Build Settings
4. Search for `User-Defined` settings
5. Add a new setting:
   - Key: `GOOGLE_MAPS_API_KEY`
   - Value: Your actual API key

### How It Works

The Podfile automatically loads the `GoogleService.xcconfig` file and merges its settings into the Runner target's build configuration. This makes the API key available as an environment variable during the build process.

The `GoogleService.xcconfig` file is already listed in `ios/.gitignore`, so your API key won't be committed to version control.

## Using the API Key in Flutter Code

Once configured, you can use Google Maps in your Flutter code:

```dart
import 'package:google_maps_flutter/google_maps_flutter.dart';

GoogleMap(
  initialCameraPosition: CameraPosition(
    target: LatLng(37.7749, -122.4194),
    zoom: 11,
  ),
)
```

The API key is automatically picked up by the native Android and iOS GoogleMaps implementations.

## Troubleshooting

### Android

**Error: "Google Maps Platform rejected your request"**
- Verify your API key is correctly set in `android/local.properties`
- Check that the API key has the correct Android app restriction configured in Google Cloud Console
- Ensure the package name matches your app's `applicationId` in `build.gradle.kts`

**Error: "BuildConfig.DEBUG" or similar**
- Run `flutter clean` and `flutter pub get`
- Rebuild with `flutter run`

### iOS

**Error: "Google Maps API key invalid"**
- Verify your API key is correctly set in `ios/Runner/GoogleService.xcconfig`
- Check that the API key has the correct iOS app restriction configured in Google Cloud Console
- Ensure the bundle identifier matches your app's identifier in Xcode

**Info.plist not reading the key**
- Clear derived data: `rm -rf ios/Pods ios/Podfile.lock build/`
- Run `flutter clean` and `flutter pub get`
- Rebuild with `flutter run`

## Security Best Practices

1. **Keep API Keys Secret**: Never commit `local.properties` (Android) or `GoogleService.xcconfig` (iOS) to version control
2. **Use Key Restrictions**: In Google Cloud Console, restrict your API key to:
   - Android apps (with SHA-1 fingerprints)
   - iOS apps (with bundle identifiers)
3. **Rotate Keys Regularly**: Generate new API keys and replace old ones periodically
4. **Monitor Usage**: Check Google Cloud Console for unusual API usage patterns
5. **Different Keys per Environment**: Consider using separate API keys for development, staging, and production

## Regenerating Local Configuration Files

If you need to regenerate these files:

1. **Android**: The `local.properties` file is created by Android Studio or can be manually created in the `android/` directory
2. **iOS**: You can manually create `ios/Runner/GoogleService.xcconfig` with the template provided above

## References

- [Google Maps Flutter Package Documentation](https://pub.dev/packages/google_maps_flutter)
- [Google Maps API Console](https://console.cloud.google.com/)
- [Secrets Gradle Plugin](https://developers.google.com/maps/flutter-package/config#android)
- [iOS Configuration Guide](https://developers.google.com/maps/flutter-package/config#ios)
