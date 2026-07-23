# React Native Expo Authentication Architecture — Complete Guide

> A single-file, interactive documentation website that teaches you **WHY** every authentication file exists, **WHEN** it should be created, **WHO** uses it, and **HOW** the entire system evolves from an empty project to a production-ready authentication architecture.

---

## Table of Contents

- [Overview](#overview)
- [What You'll Learn](#what-youll-learn)
- [Who This Is For](#who-this-is-for)
- [Features](#features)
- [Content Coverage](#content-coverage)
- [How to Use](#how-to-use)
- [Project Structure](#project-structure)
- [Technology Stack](#technology-stack)
- [Architecture Overview](#architecture-overview)
- [Chapter Index](#chapter-index)
- [Provider Comparison](#provider-comparison)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

Most authentication tutorials teach you **WHAT** to write. This guide teaches you **WHY** it exists.

This is a complete, self-contained HTML documentation website (no frameworks, no external dependencies) that covers every major authentication concept in React Native Expo — from the very first login screen to a full production architecture with MFA, role-based access, OAuth, token refresh, and more.

Everything lives in **one HTML file** — open it in any browser and start learning.

---

## What You'll Learn

- **Architecture from Scratch** — how authentication architecture is born from nothing
- **Dependency Graphs** — which files depend on which, who calls whom
- **28 Auth Modules** — Login, Register, OAuth, MFA, Magic Links, Session Management
- **File Creation Order** — the exact order to create auth files and WHY each must come first
- **Provider Comparison** — Firebase vs Supabase vs Clerk vs Auth0 vs AWS Cognito
- **Security Deep Dive** — JWT, refresh tokens, secure storage, OAuth, CSRF, replay attacks
- **State Machine** — every auth state, who changes it, which components react
- **Project Evolution** — watch the folder structure grow as features are added
- **Production Best Practices** — the dos, don'ts, and production checklist
- **Interview Questions** — common auth architecture interview Q&A

---

## Who This Is For

| Level | What You'll Get |
|-------|----------------|
| **Beginner** | Every concept explained from scratch. No prior auth knowledge required. |
| **Intermediate** | Understand WHY the architecture matters and how to make better decisions. |
| **Senior** | Full system design perspective, provider comparisons, production patterns. |

---

## Features

### Design & UX
- Dark Mode / Light Mode with toggle
- Responsive design (desktop, tablet, mobile)
- Sidebar navigation with expandable sections
- Search box with keyboard shortcut (Ctrl+K)
- Breadcrumb navigation
- Scroll progress bar
- Smooth scrolling
- Sticky sidebar
- Back to top button

### Learning Aids
- Expandable/collapsible sections
- Interactive cards
- Animated flow diagrams (HTML/CSS)
- Dependency diagrams
- State machine visualizations
- Folder tree explorer
- Code tabs (Minimal / Production / Bad Example)
- Syntax highlighting
- Copy buttons on all code blocks
- Notes, Warnings, Best Practices callouts
- Do / Don't comparison boxes
- Mini quizzes with explanations
- Interview questions with answers
- Key takeaways after every chapter
- Hands-on exercises

### Content
- 50+ chapters across 8 major sections
- 28 complete authentication modules
- 6 provider comparison profiles
- Full security deep dive
- Complete final project with folder structure

---

## Content Coverage

### Authentication Modules (28)

| # | Module | Description |
|---|--------|-------------|
| 1 | Login | Email/password authentication |
| 2 | Register | New account creation |
| 3 | Logout | Secure session termination |
| 4 | Forgot Password | Password recovery via email |
| 5 | Reset Password | Setting a new password via deep link |
| 6 | Email Verification | Confirming email ownership |
| 7 | Phone Authentication | SMS-based login |
| 8 | OTP Authentication | One-time password verification |
| 9 | Google Sign In | OAuth with Google |
| 10 | Apple Sign In | OAuth with Apple (App Store requirement) |
| 11 | Facebook Login | OAuth with Facebook |
| 12 | GitHub Login | OAuth with GitHub |
| 13 | Anonymous Login | Trial accounts before signup |
| 14 | Magic Link Login | Passwordless email-based auth |
| 15 | Session Restore | Persisting login across restarts |
| 16 | Refresh Token | Keeping sessions alive |
| 17 | Auto Login | Automatic session restoration |
| 18 | Session Expiration | Handling expired tokens |
| 19 | Token Refresh | Proactive token renewal |
| 20 | Delete Account | GDPR-compliant account removal |
| 21 | Change Password | Authenticated password update |
| 22 | Update Email | Changing account email |
| 23 | Multi-factor Auth (MFA) | TOTP/SMS second factor |
| 24 | Role Based Auth | Admin/Editor/Viewer access control |
| 25 | Protected Routes | Auth-required navigation |
| 26 | Guest Routes | Unauthenticated-only navigation |
| 27 | Admin Routes | Admin-only navigation |
| 28 | Profile Synchronization | Keeping user data in sync |

### Folder Structure Explained

| Folder | Purpose |
|--------|---------|
| `types/` | TypeScript type definitions |
| `config/` | External service initialization |
| `constants/` | Application-wide constants |
| `utils/` | Pure utility functions |
| `storage/` | Secure local data persistence |
| `services/` | External API communication |
| `repositories/` | Data access abstraction |
| `context/` | React Context definitions |
| `hooks/` | Custom React hooks |
| `providers/` | Provider wrapper composition |
| `components/` | Reusable UI components |
| `screens/` (app/) | Page-level route components |
| `navigation/` | Navigation configuration |
| `assets/` | Images, fonts, icons |

---

## How to Use

### Quick Start

1. Clone or download this repository
2. Open `index.html` in any modern browser
3. Start reading from the **Home** page

```bash
# Option 1: Direct file open
open index.html

# Option 2: Local server (recommended for search)
npx serve .
# Then open http://localhost:3000

# Option 3: Python
python -m http.server 8000
# Then open http://localhost:8000
```

### Navigation

- **Sidebar** — Click any chapter to navigate directly
- **Search** — Press `Ctrl+K` to search across all chapters
- **Breadcrumbs** — Click to go back to parent sections
- **Expandable sections** — Click headers to expand/collapse content
- **Code blocks** — Click "Copy" to copy code to clipboard
- **Quizzes** — Click an option to check your answer
- **Theme toggle** — Click the moon/sun icon to switch themes

### Recommended Reading Order

1. **Getting Started** — Introduction, Philosophy
2. **Architecture** — Stages 1-6 (Project Evolution)
3. **Core Files** — Types, Config, Services, Storage, Context, Hooks, Providers, Components, Screens, Navigation
4. **Auth Modules** — Login, Register, Logout (start here), then others as needed
5. **Advanced Topics** — Provider Comparison, Security, Best Practices
6. **Practice** — Interview Questions, Exercises, Final Project

---

## Project Structure

```
AuthApp/
├── index.html          # The complete documentation website (single file)
├── README.md           # This file
└── .gitignore          # Git ignore rules
```

---

## Technology Stack

| Layer | Technology |
|-------|-----------|
| Structure | HTML5 |
| Styling | CSS3 (Custom Properties, Grid, Flexbox) |
| Interactivity | Vanilla JavaScript (ES6+) |
| Syntax Highlighting | Custom CSS-based |
| Icons | Unicode/Emoji (no icon libraries) |
| External Dependencies | **None** |

**Zero dependencies.** The entire website is one self-contained HTML file.

---

## Architecture Overview

The guide teaches this complete auth architecture:

```
Screens (Login, Register, Home, Settings)
    ↓ use
Components (LoginForm, RegisterForm, ProtectedRoute)
    ↓ call
Hooks (useAuth, useSession, useTokenRefresh)
    ↓ read from
Context / Providers (AuthProvider, RootProvider)
    ↓ delegates to
Services (auth.service, user.service)
    ↓ uses
Repositories (auth.repository, user.repository)
    ↓ persists via
Storage (auth.storage) + SDK (Firebase/Supabase)
```

### File Creation Order

1. `types/` — Define contracts first
2. `config/` — Initialize external services
3. `constants/` — Application-wide values
4. `storage/` — Secure persistence layer
5. `services/` — Business logic layer
6. `repositories/` — Data access abstraction (optional)
7. `context/` — Global state definitions
8. `hooks/` — Clean API for components
9. `providers/` — Compose context providers
10. `components/` — Reusable UI
11. `screens/` (app/) — Page-level routes
12. **Protect navigation** — Wire up auth guards

Each step exists because the previous step created a need for it.

---

## Chapter Index

### Getting Started
- Introduction
- Philosophy

### Architecture
- Stage 1: Empty Project
- Stage 2: First Login
- Stage 3: Services Layer
- Stage 4: Hooks & Context
- Stage 5: Providers & Navigation Guard
- Stage 6: Full Architecture
- Complete Folder Structure
- Folder Evolution Timeline
- File Creation Order
- Authentication State Machine

### Core Files
- `types/` — Type Definitions
- `constants/` — Application Constants
- `config/` — Service Configuration
- `services/` — API Communication
- `repositories/` — Data Access Layer
- `storage/` — Secure Storage
- `context/` — React Context
- `hooks/` — Custom Hooks
- `providers/` — Provider Composition
- `components/` — Reusable UI
- `screens/` — Page Components
- `navigation/` — Auth-Aware Navigation

### Auth Modules
- Login, Register, Logout
- Forgot Password, Reset Password
- Email Verification
- Phone Auth, OTP Auth
- Google, Apple, Facebook, GitHub Sign In
- Anonymous Login, Magic Link
- Session Restore, Refresh Token, Auto Login
- Session Expiration
- Delete Account, Change Password, Update Email
- Profile Synchronization
- Multi-factor Authentication
- Role-Based Auth
- Protected Routes, Guest Routes, Admin Routes

### Dependency Graphs
- Login Dependencies
- Register Dependencies
- Full Dependency Map

### Advanced Topics
- Provider Comparison (Firebase, Supabase, Clerk, Auth0, Cognito)
- Security Deep Dive
- Best Practices
- Interview Questions
- Exercises
- Final Project

---

## Provider Comparison

| Feature | Firebase | Supabase | Clerk | Auth0 | AWS Cognito |
|---------|----------|----------|-------|-------|-------------|
| Setup | Easy | Easy | Easiest | Medium | Complex |
| Free Tier | Generous | Generous | 10K MAU | 7K MAU | 50K MAU |
| Email/Password | ✅ | ✅ | ✅ | ✅ | ✅ |
| OAuth | ✅ All | ✅ All | ✅ All | ✅ All | ✅ All |
| Phone Auth | ✅ | ✅ | ✅ | ✅ | ✅ |
| MFA | ✅ TOTP | ✅ TOTP | ✅ Built-in UI | ✅ Multi | ✅ SMS/TOTP |
| Offline Support | ✅ Firestore | ❌ | ❌ | ❌ | ❌ |
| Best For | Most apps | Open source | Rapid dev | Enterprise | AWS ecosystem |

---

## Key Security Concepts Covered

- JWT (JSON Web Token) structure and lifecycle
- Access Token vs Refresh Token
- Token rotation and expiration
- Secure storage with `expo-secure-store`
- Why NOT to use `AsyncStorage` for tokens
- OAuth 2.0 flow
- CSRF, XSS, replay attack prevention
- Brute force protection
- Environment variable management
- Production security checklist

---

## Contributing

This is a learning resource. If you find:
- **Errors** in code examples
- **Outdated** information
- **Missing** concepts
- **Improvements** to explanations

Please open an issue or submit a pull request.

---

## License

This project is open source and available for educational use.

---

## Acknowledgments

Built as a comprehensive learning resource for the React Native Expo community. Designed to feel like a mixture of:

- React Native Documentation
- Expo Documentation
- System Design Course
- Clean Architecture Course
- Interactive Programming Book
- Software Engineering Roadmap

---

**Start learning →** Open `index.html` in your browser.
