# Flutter Tutorial Projects

A collection of Flutter tutorial projects demonstrating various concepts, patterns, and best practices for building mobile applications with Flutter.

## 📚 Projects Overview

### 1. Basics
**Location:** `basics/`

A foundational Flutter project introducing core concepts:
- Stateful and stateless widgets
- Custom gradient containers
- Interactive dice roller
- Basic widget composition and styling

**Key Concepts:**
- Widget lifecycle
- State management basics
- Custom styling and colors
- Asset integration

---

### 2. Advanced Basics (Quiz App)
**Location:** `adv_basics/`

An interactive quiz application building upon fundamental concepts:
- Multiple screen navigation
- Data models and collections
- User interaction handling
- Results summary with question review

**Key Concepts:**
- Screen transitions
- State management across screens
- Data modeling
- List rendering and mapping
- User input handling

---

### 3. Expense Tracker
**Location:** `expense_tracker/`

A personal expense tracking application with advanced UI features:
- Add, edit, and delete expenses
- Category-based organization
- Light and dark theme support
- Responsive design

**Key Concepts:**
- Forms and user input validation
- Theme management
- CRUD operations
- Material Design 3
- Color schemes and theming

---

### 4. Meals App
**Location:** `meals/`

A meals browsing and favorites management application:
- Browse meals by category
- Filter meals by dietary preferences
- Favorite meals management
- Tab-based navigation

**Key Concepts:**
- Riverpod state management
- Provider pattern
- Tab navigation
- Filtering and searching
- Google Fonts integration

---

### 5. Shopping List (Grocery List)
**Location:** `shopping_list/`

A grocery list application with Firebase backend integration:
- Add new grocery items with categories
- Delete items from the list
- Category-based organization with custom colors
- Dark theme UI
- HTTP requests to Firebase Realtime Database
- State management with async operations

**Key Concepts:**
- HTTP client integration
- Firebase Realtime Database
- Async/await patterns
- Future handling
- JSON parsing and serialization
- CRUD operations with backend
- Error handling

---

### 6. Favorite Places
**Location:** `favorite_places/`

A location-based application for discovering, saving, and managing favorite places:
- Add places with photos and current location
- Interactive Google Maps visualization
- Capture images from camera or gallery
- Get location coordinates and addresses via geocoding
- Local persistence using SQLite database
- Place details with location information

**Key Concepts:**
- Google Maps integration
- Platform-specific APIs (location, camera)
- Image picker and file handling
- Riverpod state management
- SQLite database for persistence
- HTTP requests for geocoding API
- Async/await patterns
- Google Fonts typography

---

### 7. Chat App
**Location:** `chat_app/`

A real-time chat application with Firebase integration:
- User authentication (sign up, login)
- Real-time messaging with Firestore
- User profile image upload
- Responsive chat UI
- Platform support for mobile, web, and desktop

**Key Concepts:**
- Firebase Authentication
- Cloud Firestore database
- Image upload and storage
- Stream-based UI updates
- Custom widgets for chat bubbles and message input
- Platform adaptation

---

## 🚀 Getting Started

### Prerequisites
- Flutter SDK (latest stable version)
- Dart SDK
- An IDE (VS Code, Android Studio, or IntelliJ IDEA)
- iOS Simulator (for macOS) or Android Emulator

### Installation

1. Clone this repository:
```bash
git clone https://github.com/EslamElMeniawy/flutter-tutorial.git
cd flutter-tutorial
```

2. Navigate to any project folder:
```bash
cd basics
```

3. Install dependencies:
```bash
flutter pub get
```

4. Run the project:
```bash
flutter run
```

---

## 📱 Running on Different Platforms

Each project supports multiple platforms:

```bash
# Run on iOS Simulator
flutter run -d ios

# Run on Android Emulator
flutter run -d android

# Run on Web
flutter run -d chrome

# Run on macOS
flutter run -d macos

# Run on Linux
flutter run -d linux

# Run on Windows
flutter run -d windows
```

---

## 🛠️ Project Structure

Each project follows standard Flutter architecture:

```
project/
├── lib/              # Main application code
├── assets/           # Images, fonts, and other assets
├── test/             # Unit and widget tests
├── android/          # Android-specific configuration
├── ios/              # iOS-specific configuration
├── web/              # Web-specific configuration
├── macos/            # macOS-specific configuration
├── linux/            # Linux-specific configuration
├── windows/          # Windows-specific configuration
└── pubspec.yaml      # Project dependencies and metadata
```

---

## 📖 Learning Path

For optimal learning, it's recommended to explore the projects in this order:

1. **basics** - Learn fundamental Flutter concepts
2. **adv_basics** - Build upon basics with navigation and state
3. **expense_tracker** - Master theming and form handling
4. **shopping_list** - Learn HTTP integration and Firebase backend communication
5. **meals** - Understand advanced state management with Riverpod
6. **favorite_places** - Master platform integration, maps, and location services
7. **chat_app** - Build a real-time chat app with Firebase

---

## 🔧 Key Dependencies

### Basics
- `flutter` - Core framework

### Advanced Basics
- `flutter` - Core framework

### Expense Tracker
- `flutter` - Core framework
- `uuid` - Unique ID generation
- `intl` - Internationalization and date formatting

### Shopping List
- `flutter` - Core framework
- `http` - HTTP client for API requests
- `intl` - Internationalization and date formatting

### Meals
- `flutter` - Core framework
- `flutter_riverpod` - State management
- `google_fonts` - Custom fonts
- `transparent_image` - Image loading optimization

### Favorite Places
- `flutter` - Core framework
- `flutter_riverpod` - State management
- `google_maps_flutter` - Interactive maps
- `image_picker` - Camera and gallery access
- `location` - Device location services
- `http` - HTTP requests for geocoding
- `sqflite` - Local SQLite database
- `google_fonts` - Custom typography
- `uuid` - Unique ID generation
- `path_provider` - Platform-specific app directories

### Chat App
- `flutter` - Core framework
- `firebase_core` - Firebase initialization
- `firebase_auth` - User authentication
- `cloud_firestore` - Real-time database
- `firebase_storage` - Image upload and storage

---

## 📝 Notes

- Each project is self-contained and can be run independently
- Projects follow Flutter best practices and Material Design guidelines
- Code is well-commented for learning purposes
- All projects support hot reload for rapid development

---

## 🤝 Contributing

This is a tutorial repository for learning purposes. Feel free to fork and experiment with the code!

---

## 📄 License

This project is open source and available for educational purposes.

---

## 👤 Author

**Eslam El Meniawy**

- GitHub: [@EslamElMeniawy](https://github.com/EslamElMeniawy)

---

## 🌟 Acknowledgments

These projects are created for learning and teaching Flutter development concepts.

---

**Happy Coding! 🎉**
