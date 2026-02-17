# Architecture Documentation

## Overview

Favorite Places follows a layered architecture with clear separation of concerns:

```
┌─────────────────────────────────────┐
│         UI Layer (Screens)          │
│  places.dart, add_place.dart, etc   │
└────────────────────┬────────────────┘
                     │
┌────────────────────▼────────────────┐
│       State Management (Riverpod)   │
│       providers/user_places.dart    │
└────────────────────┬────────────────┘
                     │
┌────────────────────▼────────────────┐
│      Models & Services              │
│  models/, database operations       │
└─────────────────────────────────────┘
```

## Layers

### 1. UI Layer (Screens & Widgets)

**Location**: `lib/screens/` and `lib/widgets/`

**Screens**:
- `places.dart` - Main screen showing list of saved places
- `add_place.dart` - Screen to add new place with form
- `place_detail.dart` - View details of a single place
- `map.dart` - Interactive Google Map view

**Widgets**:
- `places_list.dart` - Reusable list component
- `image_input.dart` - Image capture/selection widget
- `location_input.dart` - Location input widget

**Responsibilities**:
- Display data to users
- Handle user interactions
- Dispatch state management actions

### 2. State Management Layer (Riverpod)

**Location**: `lib/providers/user_places.dart`

**Provider**: `userPlacesProvider`

**Responsibilities**:
- Manage application state (list of places)
- Handle business logic
- Coordinate with database layer
- Provide reactive updates to UI

**Key Operations**:
```dart
// Read places
final places = ref.watch(userPlacesProvider);

// Add place
ref.read(userPlacesProvider.notifier).addPlace(...);

// Delete place
ref.read(userPlacesProvider.notifier).deletePlace(id);
```

### 3. Models & Services Layer

**Location**: `lib/models/`, database operations

**Models**:
- `Place` - Data class representing a place

**Database**:
- SQLite database for persistence
- Automatic save/load operations

**Third-party Services**:
- Google Maps API (maps display)
- Image Picker (camera/gallery)
- Location service (GPS)
- Geocoding API (address lookup)

## State Flow

### Adding a Place
```
User Input (add_place.dart)
    ↓
User taps "Save"
    ↓
addPlace() called on Riverpod notifier
    ↓
Place added to state
    ↓
Place saved to SQLite database
    ↓
UI updates automatically (listeners notified)
```

### Loading Places
```
App startup
    ↓
Riverpod initializes userPlacesProvider
    ↓
Provider reads from SQLite database
    ↓
Places loaded into state
    ↓
UI displays loaded places
```

## Data Model

### Place
```dart
class Place {
  final String id;           // UUID
  final String title;        // Place name
  final String description;  // User description
  final File image;          // Image file
  final PlaceLocation location;
}

class PlaceLocation {
  final double latitude;
  final double longitude;
  final String address;
}
```

## Database Schema

### places table
| Column | Type | Description |
|--------|------|-------------|
| id | TEXT PRIMARY KEY | Unique identifier |
| title | TEXT | Place name |
| image | TEXT | Image file path |
| lat | REAL | Latitude |
| lng | REAL | Longitude |
| address | TEXT | Address string |
| description | TEXT | User description |

## Dependency Injection

Riverpod handles all dependency injection:
- `userPlacesProvider` provides the list of places
- Widgets access providers via `ref.watch()` or `ref.read()`
- No manual dependency passing needed

## Error Handling

- Platform channels (location, camera) throw platform exceptions
- Database errors handled gracefully with error states
- Network errors for geocoding API calls handled with fallbacks

## Performance Considerations

1. **List Rendering**: Uses `ListView.builder` for efficient list rendering
2. **Image Caching**: Images stored locally to avoid repeated downloads
3. **Database Queries**: SQLite queries optimized with proper indexing
4. **API Calls**: Geocoding API calls cached at model level

## Testing Strategy

### Unit Tests
- Model serialization/deserialization
- State management logic
- Utility functions

### Widget Tests
- Individual widget rendering
- User interaction handling
- State updates through Riverpod

### Integration Tests
- Full user workflows
- Database persistence
- Platform integration

## Future Improvements

1. **Caching Layer**: Add in-memory cache for frequently accessed places
2. **Offline Support**: Queue API calls when offline
3. **Pagination**: Load places in batches for large datasets
4. **Cloud Sync**: Sync places with cloud backend
5. **Analytics**: Track user interactions
6. **Search/Filter**: Search places by title or location
