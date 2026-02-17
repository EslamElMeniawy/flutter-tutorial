# Project Documentation Index

Quick navigation to all documentation for the Favorite Places project.

## 📚 Main Documentation

| Document | Purpose |
|----------|---------|
| [README.md](README.md) | Project overview, features, quick start |
| [ARCHITECTURE.md](ARCHITECTURE.md) | System design, layers, data flow |
| [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md) | Setup, development workflow, debugging |
| [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md) | Google Maps API configuration |
| [API_KEYS_CHECKLIST.md](API_KEYS_CHECKLIST.md) | API keys verification checklist |
| [lib/config/README.md](lib/config/README.md) | Configuration directory guide |

## 🎯 Quick Start

**First time setup? Start here:**

1. Read [README.md](README.md#getting-started) for overview
2. Follow [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#project-setup) for setup
3. Configure APIs using [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md) and [API_KEYS_CHECKLIST.md](API_KEYS_CHECKLIST.md)
4. Run the app with `flutter run`

## 📖 By Use Case

### I want to...

**Understand the project**
- Read [README.md](README.md) - Overview and features
- Read [ARCHITECTURE.md](ARCHITECTURE.md) - System design

**Set up the project**
- Follow [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#project-setup) - Step-by-step setup
- Use [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md) - Configure APIs

**Add a new feature**
- Review [ARCHITECTURE.md](ARCHITECTURE.md) - Understand layers
- Read [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#development-workflow) - Development patterns

**Fix API key issues**
- Consult [API_KEYS_CHECKLIST.md](API_KEYS_CHECKLIST.md) - Verification checklist
- See [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md#troubleshooting) - Troubleshooting

**Debug the application**
- Check [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#debugging) - Debugging techniques
- Review [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#common-issues--solutions) - Common issues

**Understand code structure**
- See [ARCHITECTURE.md](ARCHITECTURE.md#layers) - Code organization
- Review [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#code-organization) - File structure

**Modify state management**
- Read [ARCHITECTURE.md](ARCHITECTURE.md#state-management-layer-riverpod) - State flow
- Follow [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#modifying-state-management) - How to modify

## 📁 File Structure

```
favorite_places/
├── README.md                   # Project overview (START HERE)
├── ARCHITECTURE.md             # System design and layers
├── DEVELOPMENT_GUIDE.md        # Development setup and workflow
├── GOOGLE_MAPS_SETUP.md        # Maps API setup guide
├── API_KEYS_CHECKLIST.md       # API configuration checklist
├── PROJECT_DOCS_INDEX.md       # This file
├── pubspec.yaml                # Dependencies
├── android/                    # Android native code
├── ios/                        # iOS native code
└── lib/
    ├── main.dart              # Entry point
    ├── config/
    │   ├── README.md          # Configuration guide
    │   ├── api_keys.dart      # API keys (DO NOT COMMIT)
    │   └── api_keys.dart.template
    ├── models/
    │   └── place.dart         # Place data model
    ├── providers/
    │   └── user_places.dart   # Riverpod state management
    ├── screens/               # Full page screens
    └── widgets/               # Reusable components
```

## 🔑 Key Topics

### API Keys
- **Where to configure**: [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md)
- **What to verify**: [API_KEYS_CHECKLIST.md](API_KEYS_CHECKLIST.md)
- **Configuration dir**: [lib/config/README.md](lib/config/README.md)

### State Management
- **Architecture**: [ARCHITECTURE.md](ARCHITECTURE.md#state-management-layer-riverpod)
- **Data flow**: [ARCHITECTURE.md](ARCHITECTURE.md#state-flow)
- **How to modify**: [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#modifying-state-management)

### Database
- **Schema**: [ARCHITECTURE.md](ARCHITECTURE.md#database-schema)
- **Management**: [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#database-management)

### Testing
- **Strategy**: [ARCHITECTURE.md](ARCHITECTURE.md#testing-strategy)
- **How to run**: [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#testing)

## 🚀 Running Commands

```bash
# Initial setup
flutter pub get

# Run application
flutter run

# Debug specific device
flutter run -d <device_id>

# Analyze code
flutter analyze

# Run tests
flutter test

# Build release
flutter build apk          # Android APK
flutter build appbundle    # Android App Bundle
flutter build ios          # iOS build
```

See [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md) for more commands.

## 🆘 Troubleshooting

**Issue**: "API key not valid"
→ [API_KEYS_CHECKLIST.md](API_KEYS_CHECKLIST.md#troubleshooting)

**Issue**: "Google Maps not displaying"
→ [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md#troubleshooting)

**Issue**: "Build errors"
→ [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#common-issues--solutions)

**Issue**: "Location not working"
→ [README.md](README.md#troubleshooting)

## 📞 Getting Help

1. **Check the docs**: Use the index above to find relevant documentation
2. **Review architecture**: Understand [ARCHITECTURE.md](ARCHITECTURE.md)
3. **Check troubleshooting**: See relevant troubleshooting sections
4. **Flutter resources**: [Flutter Docs](https://docs.flutter.dev/)

## 📋 Checklist for New Developers

- [ ] Read [README.md](README.md)
- [ ] Review [ARCHITECTURE.md](ARCHITECTURE.md)
- [ ] Complete setup in [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md)
- [ ] Configure API keys using [GOOGLE_MAPS_SETUP.md](GOOGLE_MAPS_SETUP.md)
- [ ] Run and test the app
- [ ] Explore code structure in `lib/`
- [ ] Review [DEVELOPMENT_GUIDE.md](DEVELOPMENT_GUIDE.md#development-workflow) for contribution guidelines

## 📈 Next Steps

After setup:
1. Explore the codebase in `lib/screens/` and `lib/widgets/`
2. Review the Riverpod provider in `lib/providers/user_places.dart`
3. Try modifying a screen or widget
4. Use hot reload to see changes instantly
5. Implement a new feature following the architecture

---

**Last Updated**: February 2026  
**Project**: Favorite Places - Flutter Tutorial Series
