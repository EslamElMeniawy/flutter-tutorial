# API Keys Configuration

This directory contains API key configuration for the Favorite Places app.

## Setup

1. Copy `api_keys.dart.template` to `api_keys.dart`:
   ```bash
   cp lib/config/api_keys.dart.template lib/config/api_keys.dart
   ```

2. Open `api_keys.dart` and replace the placeholder with your actual Google Maps API key:
   - Get your API key from [Google Cloud Console](https://console.cloud.google.com/google/maps-apis)
   - Enable both Maps Static API and Geocoding API for your key

3. The `api_keys.dart` file is automatically excluded from version control via `.gitignore`

## Security Notes

- **Never commit `api_keys.dart` to version control**
- The template file (`api_keys.dart.template`) can be safely committed
- Always keep your API keys secure and rotate them if exposed

## Required APIs

The following Google Maps APIs must be enabled for your API key:
- Maps Static API (for displaying location previews)
- Geocoding API (for reverse geocoding coordinates to addresses)
