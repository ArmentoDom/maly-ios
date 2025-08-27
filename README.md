# Maly iOS App

A native iOS application for the Maly social networking platform, built with SwiftUI.

## Features

- **User Registration**: Complete registration with all profile fields including interests, moods, location, etc.
- **User Login**: Secure authentication with username/email and password
- **Profile Display**: View authenticated user profile information
- **Session Management**: Automatic authentication state management
- **Error Handling**: User-friendly error messages and loading states

## Architecture

- **SwiftUI**: Modern declarative UI framework
- **MVVM Pattern**: Clean separation of concerns with View Models
- **Async/Await**: Modern Swift concurrency for API calls
- **URLSession**: Native networking with cookie support for session management

## Project Structure

```
MalyiOS/
├── MalyiOS.xcodeproj/          # Xcode project file
└── MalyiOS/                    # Source code
    ├── MalyiOSApp.swift        # App entry point
    ├── ContentView.swift       # Main content coordinator
    ├── Views/
    │   ├── AuthenticationView.swift  # Auth mode switcher
    │   ├── LoginView.swift          # Login form
    │   ├── RegistrationView.swift   # Registration form
    │   └── MainView.swift           # Authenticated user view
    ├── Models/
    │   └── User.swift              # Data models and API structures
    ├── ViewModels/
    │   └── AuthenticationViewModel.swift  # Authentication state management
    ├── Services/
    │   └── APIService.swift        # Network layer
    └── Assets.xcassets/           # App assets and icons
```

## Setup Instructions

### 1. Configure API Base URL

Before building, update the `baseURL` in `APIService.swift`:

```swift
// For local development (default)
private let baseURL = "http://localhost:5000/api"

// For Replit deployment, use your repl's public URL:
// private let baseURL = "https://your-repl-name.your-username.repl.co/api"
```

### 2. Build and Run

1. Open `MalyiOS.xcodeproj` in Xcode
2. Select your target device (iOS Simulator or physical device)
3. Build and run the project (⌘R)

### 3. Test Authentication

1. **Register a new account**:
   - Switch to "Register" tab
   - Fill in required fields (username, email, password, full name)
   - Optionally add interests, moods, location, etc.
   - Tap "Create Account"

2. **Login with existing account**:
   - Switch to "Login" tab
   - Enter username/email and password
   - Tap "Login"

## API Integration

The app integrates with the following Maly API endpoints:

- `POST /api/register` - User registration
- `POST /api/login` - User authentication
- `POST /api/logout` - User logout
- `GET /api/auth/check` - Authentication status

### Authentication Flow

1. **Session-based**: Uses HTTP cookies for session management
2. **Automatic check**: Checks authentication status on app launch
3. **Persistent sessions**: Sessions persist between app launches
4. **Error handling**: Graceful handling of network and authentication errors

## User Registration Fields

### Required Fields
- Username (min 3 characters)
- Email (valid email format)
- Password (min 6 characters)
- Full Name

### Optional Fields
- Current Location
- Profession
- Age
- Gender
- Next Location
- Interests (multiple selection)
- Current Vibes/Moods (multiple selection)

## Key Features

### Form Validation
- Real-time validation for required fields
- Email format validation
- Password length requirements
- Username length requirements

### UI/UX
- Clean, modern SwiftUI interface
- Segmented control for login/register switching
- Tag-based selection for interests and moods
- Loading states and error messages
- Responsive layout for different screen sizes

### Error Handling
- Network error handling
- API error message display
- User-friendly error messages
- Tap-to-dismiss error notifications

## Development Notes

- **iOS 17.5+**: Minimum deployment target
- **Swift 5.0**: Language version
- **No external dependencies**: Uses only native iOS frameworks
- **Cookie support**: Automatic session cookie management
- **Async/await**: Modern concurrency for all network calls

## Testing

To test the app:

1. Ensure your Maly server is running on the configured URL
2. Test both registration and login flows
3. Verify session persistence by closing and reopening the app
4. Test with both valid and invalid credentials
5. Test network connectivity edge cases

## Troubleshooting

### Common Issues

1. **Connection refused**: Ensure the server URL is correct and accessible
2. **Registration fails**: Check server logs for validation errors
3. **Login fails**: Verify credentials and server authentication logic
4. **Session not persisting**: Check cookie configuration on both client and server

### Debug Tips

- Enable network logging in `APIService.swift`
- Check Xcode console for API response details
- Verify server is running and accessible
- Test API endpoints directly with curl or Postman