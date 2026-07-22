<div align="center">

# AuthApp

### Complete Authentication System for React Native (Expo)

Login · Register · Logout · Persistent Sessions · Protected Routes

![Expo](https://img.shields.io/badge/Expo-54-000020?style=for-the-badge&logo=expo&logoColor=white)
![React Native](https://img.shields.io/badge/React_Native-0.81-61DAFB?style=for-the-badge&logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/NativeWind-4.2-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)

</div>

---

## Overview

A full-featured authentication flow built with Expo Router and React Context. Supports registration, login, logout, token persistence, and automatic session restoration — all with a clean, layered architecture.

**Features:**

- Register with name, email, and password
- Login with email and password
- Logout with session cleanup
- Persistent login (survives app restarts)
- Automatic route guarding (redirects based on auth state)
- Mock API layer (swap with real backend anytime)
- Cross-platform storage (SecureStore on native, localStorage on web)

---

## Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| Framework | **Expo 54** | Cross-platform build tooling |
| Navigation | **Expo Router 6** | File-based routing |
| UI | **React Native 0.81** | Mobile UI components |
| Styling | **NativeWind 4** | Tailwind CSS for React Native |
| State | **React Context** | Global auth state management |
| Storage | **expo-secure-store** | Token persistence (encrypted) |
| Types | **TypeScript 5.9** | Type safety |

---

## Project Structure

```
AuthApp/
├── app/                        # Routes (Expo Router)
│   ├── _layout.tsx             # Root layout — wraps app in AuthProvider
│   ├── index.tsx               # Entry gate — checks auth, redirects
│   ├── (auth)/                 # Group: unauthenticated screens
│   │   ├── login.tsx           # Login screen
│   │   └── register.tsx        # Register screen
│   └── (tabs)/                 # Group: authenticated screens
│       ├── _layout.tsx         # Tab navigator
│       └── index.tsx           # Home screen
│
├── context/                    # Global state
│   └── authContext.tsx          # AuthProvider — user, login, register, logout
│
├── hooks/                      # Reusable logic
│   └── useAuth.ts              # Shortcut to consume auth context
│
├── services/                   # API communication
│   ├── auth.ts                 # Auth endpoints (login, register, getProfile)
│   └── api.ts                  # Generic HTTP client with token header
│
├── types/                      # TypeScript definitions
│   └── auth.ts                 # User, AuthResponse, AuthContextType
│
├── utils/                      # Pure helpers
│   ├── storage.ts              # Token persistence (SecureStore / localStorage)
│   └── validator.ts            # Input validation (email, password)
│
├── assets/                     # Static files (icons, splash)
├── components/                 # Reusable UI components
├── constants/                  # Static config values
│
├── auth-guide.html             # Interactive learning guide
└── README.md
```

---

## How It Works

### Data Flow

```
Screen (app/)
  → calls useAuth() hook
    → reads from AuthContext
      → calls service (services/auth.ts)
        → service calls backend / mock
          → returns { token, user }
        ← token saved via storage util
        ← user set in context state
      ← context re-renders providers
    ← hook returns new state
  ← screen navigates based on auth state
```

### Auth States

| State | `user` value | Token | Screen |
|-------|-------------|-------|--------|
| Not logged in | `null` | None | Login / Register |
| Logged in | `{ id, email, name }` | Saved to storage | Home (Tabs) |
| Logged out | `null` | Removed | Login |

### On App Start

```
App launches
  → AuthProvider mounts
    → useEffect runs
      → getToken() checks storage
        → Token found → getProfile() → setUser(userData)
        → No token → user stays null
    → isLoading = false
  → index.tsx re-renders
    → user exists? → Redirect to /(tabs)
    → no user?    → Redirect to /(auth)/login
```

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) 18+
- [Expo CLI](https://docs.expo.dev/get-started/installation/) installed globally

### Installation

```bash
# Clone the repository
git clone <your-repo-url>
cd AuthApp

# Install dependencies
npm install

# Start the development server
npx expo start
```

### Running

```bash
# Web
npm run web

# Android
npm run android

# iOS
npm run ios
```

---

## API Layer

The app uses a mock API that simulates real network calls. To connect to a real backend:

### Mock Behavior

```typescript
// services/auth.ts
// Register: always succeeds, returns mock token + user
// Login: accepts any email with password "password"
// getProfile: returns mock user data
```

### Connecting a Real Backend

Replace the mock functions in `services/auth.ts`:

```typescript
const API_URL = 'https://your-api.com';

export async function loginUser(email: string, password: string) {
    const response = await fetch(`${API_URL}/auth/login`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ email, password }),
    });
    if (!response.ok) throw new Error('Invalid credentials');
    return response.json(); // { token, user }
}

export async function registerUser(name: string, email: string, password: string) {
    const response = await fetch(`${API_URL}/auth/register`, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ name, email, password }),
    });
    if (!response.ok) throw new Error('Registration failed');
    return response.json(); // { token, user }
}
```

Then update `services/api.ts` to point to your real API URL.

---

## Adding New Screens

### Authenticated Screen

Create a file in `app/(tabs)/`:

```tsx
// app/(tabs)/profile.tsx
import { useAuth } from '../../hooks/useAuth';

export default function Profile() {
    const { user, logout } = useAuth();

    return (
        <View>
            <Text>{user?.name}</Text>
            <Button title="Logout" onPress={logout} />
        </View>
    );
}
```

### Unauthenticated Screen

Create a file in `app/(auth)/`:

```tsx
// app/(auth)/forgot-password.tsx
import { Link } from 'expo-router';

export default function ForgotPassword() {
    return (
        <View>
            <Text>Reset your password</Text>
            <Link href="/(auth)/login">Back to Login</Link>
        </View>
    );
}
```

---

## Architecture Principles

| Principle | How It's Applied |
|-----------|-----------------|
| **Single Responsibility** | Each file does exactly one thing |
| **Separation of Concerns** | UI / Logic / State / Network / Storage are separate |
| **DRY** | `useAuth()` hook eliminates repeated context logic |
| **Type Safety** | TypeScript interfaces for all data shapes |
| **Platform Awareness** | Storage utility handles native vs web differences |
| **Fail Gracefully** | AuthProvider catches invalid tokens and cleans up |

---

## Learning Resources

The `auth-guide.html` file in the project root is an interactive learning guide with:

- Complete flow diagrams for register, login, and logout
- Line-by-line code explanations
- Route guard logic breakdown
- A working browser demo that simulates the same auth logic

Open it in your browser:

```bash
# macOS
open auth-guide.html

# Linux
xdg-open auth-guide.html

# Windows
start auth-guide.html
```

---

## License

MIT
