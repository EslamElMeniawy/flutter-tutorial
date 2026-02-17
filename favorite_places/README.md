# Favorite Places

A Flutter application for discovering, saving, and managing your favorite places with geolocation and interactive maps.

## 📋 Overview

**Favorite Places** is a cross-platform mobile application built with Flutter that enables users to:
- 📍 Add new places with photos and current location
- 🗺️ View places on interactive Google Maps
- 📸 Capture or select images from gallery
- 🔍 Get location coordinates and addresses
- 💾 Persist places data locally using SQLite
- ✨ View detailed information about saved places

This project demonstrates advanced Flutter concepts including state management with Riverpod, platform-specific APIs, and database integration.

## 🎯 Features

- **Place Management**
  - Add new favorite places with title and description
  - Delete saved places
  - View all saved places in a list

- **Image Capture**
  - Take photos directly from the camera
  - Pick images from device gallery
  - Preview images in place details

- **Geolocation**
  - Get current device location
  - View location on interactive Google Map
  - Display location coordinates and address

- **Data Persistence**
  - Local storage using SQLite database
  - Automatic data recovery on app restart

- **Maps Integration**
  - Interactive Google Maps view
  - Zoom and pan capabilities
  - Static map preview for places list

## 🏗️ Project Structure

```
lib/
├── main.dart                 # App entry point and theme configuration
├── config/
│   ├── api_keys.dart        # API configuration (template provided)
│   ├── api_keys.dart.template
│   └── README.md            # Config documentation
├── models/
│   └── place.dart           # Place data model
├── providers/
│   └── user_places.dart     # Riverpod state management for places
├── screens/
│   ├── places.dart          # Main places list screen
│   ├── add_place.dart       # Add new place screen
│   ├── place_detail.dart    # Place details screen
│   └── map.dart             # Google Maps screen
└── widgets/
    ├── places_list.dart     # Places list UI component
    ├── image_input.dart     # Image capture/selection widget
    └── location_input.dart  # Location input widget
```

## 🛠️ Technology Stack

| Technology | Purpose |
|------------|---------|
| **Flutter** | UI framework |
| **Dart** | Programming language |
| **Riverpod** | State management |
| **SQLite** (sqflite) | Local database |
| **Google Maps Flutter** | Interactive maps |
| **Image Picker** | Camera & gallery access |
| **Location** | Device location access |
| **Google Fonts** | Custom fonts |
| **UUID** | Unique ID generation |
| **HTTP** | API calls for geocoding |

## 📦 Dependencies

Key packages used in this project:
- `flutter_riverpod: ^3.2.1` - State management
- `google_maps_flutter: ^2.14.2` - Interactive maps
- `image_picker: ^1.2.1` - Photo selection
- `location: ^8.0.1` - GPS location services
- `sqflite: ^2.4.2` - Local database
- `http: ^1.6.0` - HTTP requests
- `google_fonts: ^8.0.1` - Custom typography
- `uuid: ^4.5.2` - ID generation

See [pubspec.yaml](pubspec.yaml) for the complete list of dependencies.

## 🚀 Getting Started

### Prerequisites

Before running this project, ensure you have:
- Flutter SDK installed ([Installation Guide](https://flutter.dev/docs/get-started/install))
- Dart SDK (included with Flutter)
- A physical device or emulator for testing
- Google Maps API keys (see setup guide below)

### Installation

1. **Clone or navigate to the project**
   ```bash
   cd favorite_places
   ```

2. **Get dependencies**
   ```bash
   flutter pub get
   ```

3. **Configure API Keys**
   
   This project requires Google Maps API keys. Follow the detailed setup guide:
   - [Google Maps Setup Guide](GOOGLE_MAPS_SETUP.md) - Complete instructions
   - [API Keys Checklist](API_KEYS_CHECKLIST.md) - Configuration verification

   Quick summary:
   - Generate 3 API keys in [Google Cloud Console](https://console.cloud.google.com/)
   - Add Android key to `android/local.properties`
   - Add iOS key to `ios/Runner/GoogleService.xcconfig`
   - Add HTTP calls key to `lib/config/api_keys.dart`

4. **Run the app**
   ```bash
   flutter run
   ```

## 📱 Platform-Specific Setup

### Android
- Minimum SDK: 21
- Requires permissions in `AndroidManifest.xml`:
  - Location access
  - Camera access
  - Photo gallery access
- API key configured via `android/local.properties` and Secrets Gradle Plugin

### iOS
- Minimum target: iOS 12.0
- Requires permissions in `Info.plist`:
  - Location access (NSLocationWhenInUseUsageDescription)
  - Camera access (NSCameraUsageDescription)
  - Photo library access (NSPhotoLibraryUsageDescription)
- API key configured via `ios/Runner/GoogleService.xcconfig`

## 🔐 Security

- **API Keys**: Secured using platform-specific methods (Gradle secrets for Android, Xcode config for iOS)
- **Local Storage**: All data stored locally in SQLite database
- **No Server Communication**: Except for geocoding API calls using secure HTTP

For detailed security information, see:
- [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md)
- [API_KEYS_CHECKLIST.md](API_KEYS_CHECKLIST.md)

## 🏗️ Architecture

### State Management (Riverpod)
The app uses Riverpod for state management through the `user_places` provider, which manages:
- List of saved places
- Add/delete operations
- Database persistence

### Data Model
- **Place**: Contains title, description, image path, location (lat/lng), address, and ID

### Database
- SQLite database for persistent storage
- Structured schema for place data
- Migration-ready architecture

## 📸 Screenshots & Usage

### Main Workflow
1. **View Places**: Launch app to see saved places list
2. **Add Place**: Tap floating button to add a new place
3. **Capture Details**:
   - Enter title and description
   - Take/select photo
   - Capture current location or pick on map
4. **Save**: Place is stored locally and added to list
5. **View Details**: Tap any place to see full details and map

## 🐛 Troubleshooting

### Common Issues

**Google Maps not displaying**
- Verify API keys are correctly configured
- Check that required APIs are enabled in Google Cloud Console
- Ensure wait 5-10 minutes after enabling APIs (propagation delay)
- See [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md)

**Location not working**
- Check location permissions are granted in device settings
- Ensure location service is enabled on device
- Use real device for accurate GPS; emulator may have location delays

**Images not saving**
- Verify camera and gallery permissions are granted
- Check device storage availability

**Database errors**
- Ensure app has write permissions
- Try clearing app data and reinstalling

For more troubleshooting steps, see [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md) and [API_KEYS_CHECKLIST.md](API_KEYS_CHECKLIST.md).

## 📚 Learning Resources

This project demonstrates several advanced Flutter concepts:
- **State Management**: Riverpod for reactive programming
- **Platform Channels**: Access native Android/iOS APIs
- **Async/Await**: Handling asynchronous operations
- **Database**: Local data persistence with SQLite
- **API Integration**: HTTP requests for geocoding
- **Image Processing**: Camera and gallery integration

### Useful Links
- [Flutter Documentation](https://docs.flutter.dev/)
- [Riverpod Documentation](https://riverpod.dev/)
- [Google Maps Flutter Plugin](https://pub.dev/packages/google_maps_flutter)
- [SQLite with Flutter](https://pub.dev/packages/sqflite)

## 📄 Additional Documentation

- [lib/config/README.md](lib/config/README.md) - Configuration setup
- [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md) - Detailed Google Maps API setup
- [API_KEYS_CHECKLIST.md](API_KEYS_CHECKLIST.md) - API key configuration checklist

## 📝 License

This project is part of the Flutter Tutorial series.

## 🤝 Contributing

This is an educational tutorial project. Modifications are welcome for learning purposes.
