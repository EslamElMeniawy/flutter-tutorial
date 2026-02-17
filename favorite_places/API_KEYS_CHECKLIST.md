# Google Maps API Keys Configuration Checklist

Use this checklist to verify your API keys are properly configured in Google Cloud Console.

## Key 1: Android Native SDK
**Key ID**: `AIzaSyDcc487-PMkw9vypxr_bY8LPkIWm6u-6D0`  
**Location**: `android/local.properties`

### Required APIs
- [ ] Maps SDK for Android

### Restrictions (Recommended)
- [ ] **Application restrictions**: Android apps
- [ ] **Add bundle ID**: `com.example.favorite_places` (or your actual bundle ID)

---

## Key 2: iOS Native SDK  
**Key ID**: `AIzaSyCNVjjf6aQCwLtzDdvi_xD9pBoCoMuL2Y0`  
**Location**: `ios/Runner/GoogleService.xcconfig`

### Required APIs
- [ ] Maps SDK for iOS

### Restrictions (Recommended)
- [ ] **Application restrictions**: iOS apps
- [ ] **Add bundle ID**: `com.example.favoritePlaces` (or your actual bundle ID)

---

## Key 3: API Calls (HTTP Requests)
**Key ID**: `AIzaSyDLcwxUggpPZo8lcbH0TB4Crq5SJjtj4ag`  
**Location**: `lib/config/api_keys.dart`

### Required APIs
- [ ] Maps Static API (for static map images)
- [ ] Geocoding API (for address lookup)

### Restrictions (Recommended)
- [ ] **Application restrictions**: None (allows requests from mobile devices)
- [ ] **API restrictions**: Restrict to only "Maps Static API" and "Geocoding API"

---

## How to Configure in Google Cloud Console

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Select your project
3. Navigate to **APIs & Services** > **Credentials**
4. Click on each API key to configure it:
   - Enable required APIs under **API restrictions**
   - Set **Application restrictions** as shown above
5. Enable the required APIs:
   - Navigate to **APIs & Services** > **Library**
   - Search for and enable each required API

---

## Testing Your Setup

### Test Android Native Key
```bash
flutter run -d android
# Should display interactive Google Map successfully
```

### Test iOS Native Key
```bash
flutter run -d ios
# Should display interactive Google Map successfully
```

### Test API Calls Key
- Add a new place with location
- Verify the static map preview appears
- Verify the address is populated correctly

---

## Troubleshooting

### "API key not valid" error
- Ensure the correct APIs are enabled for that specific key
- Check that application restrictions match your bundle ID
- Wait 5-10 minutes after making changes (propagation time)

### Static map not showing
- Verify Maps Static API is enabled for the API calls key
- Check network connectivity
- Look for error messages in debug console

### Address not resolving
- Verify Geocoding API is enabled for the API calls key
- Check API quota/billing in Google Cloud Console
