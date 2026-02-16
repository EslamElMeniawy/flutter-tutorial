# Firebase Setup

## Initial Setup

1. Install FlutterFire CLI:
   ```bash
   dart pub global activate flutterfire_cli
   ```

2. Run FlutterFire configuration:
   ```bash
   flutterfire configure
   ```

3. Follow the prompts to:
   - Select your Firebase project
   - Choose Android and iOS platforms
   - Authorize with your Google account

This will automatically generate the following files:
- `android/app/google-services.json`
- `ios/Runner/GoogleService-Info.plist`
- `lib/firebase_options.dart`

## For Team Members

When cloning this repository for the first time:

1. Install dependencies:
   ```bash
   flutter pub get
   ```

2. Set up Firebase configuration:
   ```bash
   flutterfire configure
   ```

3. Select the appropriate Firebase project and platforms

**Note:** The Firebase configuration files are listed in `.gitignore` and are not tracked by git. Each developer or environment needs their own configuration generated via `flutterfire configure`.

## Important Security Notes

⚠️ **DO NOT commit the following files:**
- `android/app/google-services.json`
- `ios/Runner/GoogleService-Info.plist`
- `lib/firebase_options.dart`
- `firebase.json`

These files contain sensitive API keys and project credentials that should never be stored in version control.

## Troubleshooting

If you encounter issues:
- Ensure you have the latest Flutter SDK: `flutter upgrade`
- Clear pub cache: `flutter clean && flutter pub get`
- Regenerate Firebase configuration: `flutterfire configure` (with `--overwrite` flag if needed)
