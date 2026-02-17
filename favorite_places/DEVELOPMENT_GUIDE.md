# Development Guide

## Prerequisites

Before contributing to this project, ensure you have:
- Flutter SDK (3.11.0 or higher)
- Dart SDK (included with Flutter)
- Android Studio or Xcode (for platform-specific development)
- Git for version control
- Google Maps API keys (see [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md))

## Project Setup

### 1. Initial Setup
```bash
# Clone the repository
cd favorite_places

# Get dependencies
flutter pub get

# Get packages for analysis
flutter pub get --upgrade

# (Optional) Generate code if using any build_runner packages
# flutter pub run build_runner build
```

### 2. API Key Configuration
Required before running the app:

1. Create `lib/config/api_keys.dart` from template:
   ```bash
   cp lib/config/api_keys.dart.template lib/config/api_keys.dart
   ```

2. Add your Google Maps API key to the file

3. Configure platform-specific keys:
   - [Android Setup](GOOGLE_MAPS_SETUP.md#android-setup)
   - [iOS Setup](GOOGLE_MAPS_SETUP.md#ios-setup)

### 3. Run the Application
```bash
# Run on default device/emulator
flutter run

# Run on specific device
flutter devices                    # List available devices
flutter run -d <device_id>

# Run with debugging
flutter run --debug

# Run with profiling
flutter run --profile

# Run in release mode
flutter run --release
```

## Code Organization

```
lib/
├── main.dart                 # App entry point
├── config/                   # Configuration files
│   ├── api_keys.dart        # API keys (DO NOT COMMIT)
│   ├── api_keys.dart.template
│   └── README.md
├── models/                   # Data models
│   └── place.dart
├── providers/                # Riverpod state management
│   └── user_places.dart
├── screens/                  # Full screens/pages
│   ├── places.dart
│   ├── add_place.dart
│   ├── place_detail.dart
│   └── map.dart
└── widgets/                  # Reusable UI components
    ├── places_list.dart
    ├── image_input.dart
    └── location_input.dart
```

## Development Workflow

### Adding a New Screen

1. Create file in `lib/screens/my_screen.dart`
2. Extend `StatelessWidget` or `StatefulWidget`
3. Implement the `build()` method
4. Use Riverpod providers for state management:
   ```dart
   @override
   Widget build(BuildContext context, WidgetRef ref) {
     final places = ref.watch(userPlacesProvider);
     return Scaffold(...);
   }
   ```

### Adding a New Reusable Widget

1. Create file in `lib/widgets/my_widget.dart`
2. Implement the widget class
3. Keep widgets focused and single-responsibility
4. Example:
   ```dart
   class MyWidget extends StatelessWidget {
     final String title;
     const MyWidget({required this.title});

     @override
     Widget build(BuildContext context) {
       return Card(child: Text(title));
     }
   }
   ```

### Modifying State Management

The app uses a single provider: `userPlacesProvider`

For changes to state:
1. Edit `lib/providers/user_places.dart`
2. Add new methods to the `UserPlacesNotifier` class
3. Use `ref.read(userPlacesProvider.notifier).methodName()`

Example:
```dart
// In screens
ref.read(userPlacesProvider.notifier).addPlace(
  title: 'My Place',
  description: 'Description',
  location: PlaceLocation(...),
  image: File(...),
);
```

## Common Tasks

### Running Specific Device

```bash
# List devices
flutter devices

# Run on device
flutter run -d <device_id>

# Run on emulator
flutter run -d emulator-5554
```

### Hot Reload & Hot Restart

During `flutter run` in terminal:

- Press `r` - Hot reload (reload code, keep app state)
- Press `R` - Hot restart (full restart, clear state)
- Press `d` - Detach from current device
- Press `q` - Quit

### Debugging

#### Print Debugging
```dart
print('Debug message: $variable');
debugPrint('Multiline\nDebug message');
```

#### Debugger
```bash
# Stop at breakpoint
flutter run

# In Android Studio: Click line number to set breakpoint
# Then interact with app to hit breakpoint
```

#### Performance Profiling
```bash
flutter run --profile

# In DevTools:
# - Memory tab: Check memory usage
# - Performance tab: Check frame rate
# - Timeline: Detailed frame analysis
```

### Code Analysis

```bash
# Run linter
flutter analyze

# Run specific lints
dart analyze lib/

# Fix issues automatically
dart fix --apply
```

### Testing

```bash
# Run all tests
flutter test

# Run specific test file
flutter test test/widget_test.dart

# Run with coverage
flutter test --coverage

# Generate coverage report
lcov --remove coverage/lcov.info 'lib/generated/*' -o coverage/filtered.lcov
genhtml coverage/filtered.lcov --output-directory coverage/html
```

## Database Management

### Local Database (SQLite)

The app uses SQLite for persistent storage.

**Database file location**:
- Android: `/data/data/com.example.favorite_places/databases/favorite_places.db`
- iOS: App Documents folder

**Viewing database**:
```bash
# Android
adb shell
cd /data/data/com.example.favorite_places/databases/
sqlite3 favorite_places.db
.tables
.schema places
SELECT * FROM places;

# iOS (with Debug app)
# Use iOS app containers browser in Xcode
```

**Resetting database**:
```bash
# Clear app data (full reset)
flutter clean
flutter pub get
```

## Working with External APIs

### Google Maps

- Interactive maps: Automatically configured via platform keys
- Static maps: Use Geocoding API from `api_keys.dart`
- See [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md) for details

### Location Services

```dart
import 'package:location/location.dart';

Location location = Location();
LocationData myLocation = await location.getLocation();
```

### Image Picker

```dart
import 'package:image_picker/image_picker.dart';

final picker = ImagePicker();
final image = await picker.pickImage(source: ImageSource.camera);
```

## Debugging with DevTools

```bash
# Start DevTools
flutter pub global activate devtools
devtools

# Connect running app to DevTools
# Copy URL from `flutter run` output and open in browser
```

### DevTools Features
- **Inspector**: Widget tree inspection
- **Performance**: Frame-by-frame performance analysis
- **Memory**: Memory allocation and leaks
- **Network**: HTTP requests inspection
- **Logging**: App logs and errors
- **Debugger**: Breakpoints and stepping

## Build and Release

### Android Release Build

```bash
# Build APK
flutter build apk

# Build App Bundle for Play Store
flutter build appbundle

# Sign and align APK
flutter build apk --split-per-abi
```

### iOS Release Build

```bash
# Build iOS app
flutter build ios

# Archive for TestFlight/App Store
flutter build ios --release
```

## Common Issues & Solutions

### API Key Issues
- See [API_KEYS_CHECKLIST.md](API_KEYS_CHECKLIST.md)
- See [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md#troubleshooting)

### Build Errors

```bash
# Clear build cache
flutter clean

# Update dependencies
flutter pub get
flutter pub upgrade

# Regenerate platform code
flutter pub get
flutter pub run build_runner clean
```

### Platform-Specific Issues

**Android**:
```bash
# Clean build
./gradlew clean  # in android/ directory
cd android && ./gradlew clean && cd ..

# Force rebuild
flutter clean && flutter pub get
```

**iOS**:
```bash
# Clean cocoapods
rm -rf ios/Pods ios/Podfile.lock
flutter pub get
flutter run
```

## Best Practices

### Code Style
- Follow Dart style guide (checked by `flutter analyze`)
- Use meaningful variable names
- Comment complex logic
- Keep functions small and focused

### State Management
- Use Riverpod providers for shared state
- Avoid lifting state unnecessarily
- Keep business logic in notifiers

### Performance
- Use `const` constructors when possible
- Implement `==` and `hashCode` in models (use `equatable` if needed)
- Profile before optimizing
- Use `ListView.builder` for long lists

### Error Handling
- Use try-catch for platform channels
- Show user-friendly error messages
- Log errors for debugging

## Resources

- [Flutter Documentation](https://docs.flutter.dev/)
- [Dart Language Tour](https://dart.dev/guides/language/language-tour)
- [Riverpod Documentation](https://riverpod.dev/)
- [Google Maps Flutter Integration](https://pub.dev/packages/google_maps_flutter)
- [Effective Dart](https://dart.dev/guides/language/effective-dart)

## Support

For issues or questions:
1. Check existing documentation in this project
2. Review Flutter official documentation
3. Check package documentation (pub.dev)
4. Use `flutter doctor` to diagnose environment issues
