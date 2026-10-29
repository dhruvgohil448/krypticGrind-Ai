<p align="center">
  <img src="https://img.shields.io/badge/Platform-iOS%2017.2+-blue?style=for-the-badge&logo=apple" />
  <img src="https://img.shields.io/badge/Swift-5.0-orange?style=for-the-badge&logo=swift" />
  <img src="https://img.shields.io/badge/SwiftUI-Framework-purple?style=for-the-badge&logo=swift" />
  <img src="https://img.shields.io/badge/AI-Gemini%202.0%20Flash-green?style=for-the-badge&logo=google" />
  <img src="https://img.shields.io/badge/License-Private-red?style=for-the-badge" />
</p>

# ⚔️ KrypticGrind

> **Your Ultimate Competitive Programming Companion** — An AI-powered iOS app that transforms your Codeforces journey into an RPG-style adventure with real-time analytics, personalized coaching, and gamified practice.

---

## 🎯 Overview

KrypticGrind is a native iOS application built entirely with **SwiftUI** that connects to the **Codeforces API** and **Google Gemini AI** to deliver a premium competitive programming companion. It tracks your submissions, analyzes your performance, identifies weaknesses, and provides personalized recommendations — all wrapped in a stunning RPG-themed interface with multiple color themes.

---

## ✨ Features

### 🏠 Home Dashboard
- **User Profile Card** — Displays your Codeforces avatar, handle, rating, and rank badge with color-coded ratings
- **Daily Streak Tracker** — GitHub-style contribution grid showing your solving activity over time
- **User Stats Overview** — At-a-glance metrics for your Codeforces profile
- **AI Suggestions Card** — Quick AI-powered topic recommendations
- **Next Contest Card** — Countdown to the next upcoming Codeforces contest
- **Camera/Scanner** — Scan a problem statement from paper or screenshot; uses **Apple Vision (OCR)** to extract text, then **Gemini AI** to provide a strategic approach guide (no spoilers — teaches *how* to think)

### 📈 Rating Analytics
- **Interactive Rating Chart** — Visualize your rating progression over time using Swift Charts
- **Contest History** — Browse past contests with rating changes
- **Performance Trends** — Identify peaks, dips, and growth patterns

### 📝 Submissions Tracker
- **Recent Submissions** — Browse your latest Codeforces submissions with verdict badges
- **Verdict Statistics** — Breakdown of Accepted, WA, TLE, MLE, etc.
- **Language Statistics** — See which programming languages you use most
- **Difficulty Distribution** — Analyze the rating spread of problems you've solved

### 🏆 Contests
- **Upcoming Contests List** — Live feed of upcoming Codeforces contests
- **Contest Details** — Start time, duration, and countdown timer for each contest
- **Contest Analytics** — AI-powered post-contest analysis with strategic insights
- **Contest Problems Browser** — View problem lists for contests with ratings and tags
- **Live Activity Widget** — iOS Dynamic Island & Lock Screen countdown timer for active contests
- **Push Notifications** — Get reminded before contests start

### ⚔️ The Dungeon (Practice & Leaderboard)

#### Training Grounds
- **Skill Trees (Tag Analysis)** — See your solved problem counts per algorithm topic (DP, Graphs, Greedy, etc.)
- **Weapon Mastery (Language Stats)** — Analyze proficiency across programming languages
- **Battle Results (Verdict Stats)** — Visual breakdown of submission outcomes
- **Challenge Levels (Difficulty Stats)** — Track what difficulty ranges you're conquering
- **AI-Powered Practice Tags** — Gemini suggests weak topics you should focus on

#### Hall of Fame (Leaderboard)
- **Friends Leaderboard** — Add Codeforces handles and compare ratings, problems solved, and contest participation
- **Real-time Updates** — Pull live data from Codeforces API for all tracked handles
- **Ranking System** — Sorted by rating with visual rank indicators

### 🤖 AI-Powered Features (Gemini 2.0 Flash)
- **Personalized Suggestions** — AI analyzes your submission history, rating, weak topics, and recent performance to generate 4-6 actionable improvement recommendations
- **Problem Recommendations** — Smart problem set generation targeting your weak areas at appropriate difficulty
- **Practice Tag Suggestions** — AI identifies the 3 most impactful topics for you to practice
- **Problem Scanner** — OCR + AI strategy guide for scanned problem statements
- **Contest Analysis** — Post-contest AI breakdown with strategies and learning opportunities

### 🎨 Theming System
Seven built-in color themes with live-switching:
| Theme | Style |
|-------|-------|
| 🌊 **Ocean** | Professional dark blue |
| 🌅 **Sunset** | Warm amber on deep navy |
| 🌲 **Forest** | Nature-inspired green |
| 🌌 **Cosmic** | Modern purple dark mode |
| ⬜ **Minimal** | Clean light mode |
| 💜 **Lavender** | Soft pastel palette |
| 🔮 **Cyberpunk** | Neon purple hacker vibes |

### 📱 Widgets & Live Activities
- **Upcoming Contests Widget** — Home screen widget (small & medium) showing next Codeforces contests
- **Contest Live Activity** — Dynamic Island + Lock Screen live countdown during contests with progress bar

### 🔔 Notifications
- Contest reminders before start time
- Foreground notification delivery with banner + sound

---

## 🏗️ Architecture

```
krypticGrind/
├── krypticGrindApp.swift              # App entry point, notification setup
├── ContentView.swift                  # Root view with tab navigation & onboarding
├── Info.plist                         # Live Activities, custom fonts config
├── krypticGrind.entitlements          # App sandbox entitlements
│
├── Models/
│   ├── CFUser.swift                   # Codeforces user data model
│   ├── Contest.swift                  # Contest model + API response types
│   ├── Submission.swift               # Submission model with verdict helpers
│   ├── ProblemNote.swift              # Problem notes & review-later system
│   ├── AIModels.swift                 # AI suggestion data structures
│   ├── ContestAnalytics.swift         # Contest standings, ratings, analytics
│   ├── LeaderboardManager.swift       # Friends leaderboard CRUD + CF API sync
│   └── LiveActivityAttributes.swift   # ActivityKit attributes for widgets
│
├── Views/
│   ├── HomeView.swift                 # Main dashboard (2400+ lines)
│   ├── RatingChartView.swift          # Rating history visualization
│   ├── SubmissionsView.swift          # Submissions browser & analytics
│   ├── ContestListView.swift          # Contest browsing & AI analysis
│   ├── DungeonPracticeView.swift      # RPG-themed practice analytics
│   ├── DungeonLeaderboardView.swift   # Friends comparison leaderboard
│   ├── AISuggestionsView.swift        # Full AI suggestions interface
│   ├── AIProblemSuggestionCard.swift  # AI problem recommendation cards
│   ├── OnboardingView.swift           # First-launch onboarding flow
│   ├── HandleInputSheet.swift         # Codeforces handle input modal
│   ├── PracticeTrackerView.swift      # Practice tracking & goals
│   ├── ReviewLaterView.swift          # Saved problems for review
│   ├── ThemeSelectorSheet.swift       # Theme picker sheet
│   ├── ThemePreviewView.swift         # Theme preview cards
│   ├── CustomTabBar.swift             # Custom bottom tab bar
│   └── LeaderboardView.swift          # Leaderboard table view
│
├── Services/
│   ├── CFService.swift                # Codeforces API client (800+ lines)
│   │                                  # - User info, ratings, submissions, contests
│   │                                  # - Network monitoring, retry w/ backoff
│   │                                  # - Fallback URLs, caching, rate limiting
│   └── GeminiService.swift            # Google Gemini AI client (750+ lines)
│                                      # - Suggestion generation & parsing
│                                      # - Problem recommendations
│                                      # - Practice tag suggestions
│                                      # - Contest analysis
│                                      # - Response caching
│
├── Utils/
│   ├── ColorPalette.swift             # 7 color themes + ColorThemeManager
│   ├── Extensions.swift               # Color, Date, Array, UserDefaults extensions
│   ├── FontExtension.swift            # Custom font registration (TT Phobos)
│   ├── IconSystem.swift               # SF Symbol icon helpers
│   ├── NotificationManager.swift      # Push notifications + Live Activities
│   └── UberTheme.swift                # Additional theme utilities
│
├── Fonts/                             # TT Phobos Trial font family (14 weights)
├── Assets.xcassets/                   # App icons, colors, images
└── Preview Content/                   # SwiftUI preview assets

ContestLiveActivityWidget/
├── ContestLiveActivityWidgetBundle.swift        # Widget bundle entry
├── ContestLiveActivityWidgetLiveActivity.swift  # Dynamic Island + Lock Screen UI
├── UpcomingContestsWidget.swift                 # Home screen contest widget
├── AppIntent.swift                              # Widget intents
└── Assets.xcassets/                             # Widget assets
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **UI Framework** | SwiftUI |
| **Charts** | Swift Charts |
| **Networking** | URLSession + async/await + Combine |
| **AI** | Google Gemini 2.0 Flash API |
| **OCR** | Apple Vision (VNRecognizeTextRequest) |
| **Camera** | VisionKit (Document Scanner) |
| **Photo Picker** | PhotosUI (PHPickerViewController) |
| **Widgets** | WidgetKit |
| **Live Activities** | ActivityKit |
| **Notifications** | UserNotifications |
| **Network Monitor** | Network (NWPathMonitor) |
| **Persistence** | UserDefaults (handles, cache, streaks) |
| **Typography** | TT Phobos Trial (custom font family) |
| **Concurrency** | Swift Concurrency (async/await, TaskGroup) |
| **Min. Deployment** | iOS 17.2+ |
| **Swift Version** | 5.0 |

---

## 🚀 Getting Started

### Prerequisites
- **Xcode 15+** (recommended: latest stable)
- **iOS 17.2+** device or simulator
- **Apple Developer Account** (free personal team is fine)

### Setup

1. **Clone the repository**
   ```bash
   git clone git@github.com:dhruvgohil448/krypticGrind-Ai.git
   cd krypticGrind-Ai
   ```

2. **Open in Xcode**
   ```bash
   open krypticGrind.xcodeproj
   ```

3. **Select your team**  
   Go to **Signing & Capabilities** and select your personal development team.

4. **Build & Run**  
   Select an iOS 17.2+ simulator or device and hit ⌘R.

### Configuration
- The app uses the **Codeforces public API** — no API key needed for CF data.
- **Gemini AI** is pre-configured with an API key in `GeminiService.swift`. For production, replace with your own key from [Google AI Studio](https://aistudio.google.com/).

---

## 📸 App Flow

```
Onboarding → Enter CF Handle → Home Dashboard
                                    │
                    ┌───────────────┼───────────────┐
                    │               │               │
              📈 Rating       📝 Submissions   🏆 Contests
              Chart View      & Analytics     List & Details
                    │               │               │
                    └───────────────┼───────────────┘
                                    │
                           ⚔️ The Dungeon
                          ┌────────┴────────┐
                    Training           Hall of
                    Grounds             Fame
                   (Practice)       (Leaderboard)
```

---

## 🎮 RPG Theme

KrypticGrind uses a dungeon/RPG metaphor throughout:
- **Training Grounds** → Practice analytics
- **Skill Trees** → Algorithm topic proficiency
- **Weapon Mastery** → Programming language stats
- **Battle Results** → Submission verdicts
- **Challenge Levels** → Difficulty distribution
- **Hall of Fame** → Friends leaderboard
- **Quest Complete!** → Pull-to-refresh animation with sword fighting effects

---

## 🔧 Key Design Decisions

- **No third-party dependencies** — The entire app is built with Apple's native frameworks for maximum stability and App Store compatibility.
- **Singleton services** — `CFService.shared` and `GeminiService.shared` provide centralized data management with `@Published` properties for reactive UI.
- **Aggressive caching** — Contest data is cached for 24 hours; AI tag suggestions are cached per-user per-day to minimize API calls.
- **Retry with exponential backoff** — Network requests retry up to 3 times with fallback URLs for Codeforces API reliability.
- **Background threading** — All network requests and heavy computations run on background queues, with UI updates dispatched to `@MainActor`.

---

## 👨‍💻 Author

**Dhruv Gohil**  
- GitHub: [@dhruvgohil448](https://github.com/dhruvgohil448)

---

## 📄 License

This project is private and not open-sourced. All rights reserved.
