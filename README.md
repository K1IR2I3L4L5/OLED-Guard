# OLED Guard

![Platform](https://img.shields.io/badge/PLATFORM-ANDROID%208.0%2B-161616?style=flat-square&labelColor=1D2021&color=2A6F62)
![Kotlin](https://img.shields.io/badge/KOTLIN-2.0-161616?style=flat-square&labelColor=1D2021&color=2A6F62)
![UI](https://img.shields.io/badge/UI-JETPACK%20COMPOSE%20M3-161616?style=flat-square&labelColor=1D2021&color=2A6F62)
![License](https://img.shields.io/badge/LICENSE-MIT-161616?style=flat-square&labelColor=1D2021&color=2A6F62)

**OLED Guard** is a lightweight, open-source utility with zero ads or trackers designed to protect AMOLED/OLED screens from display burn-in.

---

## Key Features

- **Local Protection Masks (`MaskCanvasView`)** — Hardware-accelerated dimming for the top status bar, bottom navigation bar, and static interface elements with full touch event pass-through (`FLAG_NOT_TOUCHABLE`).
- **Presets & HUD Constructor** — Ready-made templates for TikTok / YouTube Shorts / Reels, navigation apps (Yandex Maps, Google Maps), and custom coordinate-based zones `(X, Y, W, H)` for gaming HUDs.
- **Blackout Mode with Pixel Shift** — Complete physical pixel shutdown (`#000000`) over running apps, featuring dimmed text clock and battery indicator that shift positions every 30 seconds.
- **Extra Dimmer** — Reduces screen brightness below the minimum system threshold.
- **Diagnostics & Pixel Fixer** — Full-screen subpixel uniformity checker and automated color cycle / RGB noise generator to resolve image retention.
- **Automation & Quick Access** — Automatic profile switching based on currently opened apps and a dedicated **OLED Blackout** Quick Settings tile (`TileService`).

---

## Tech Stack & Architecture

- **Language:** 100% Kotlin
- **UI:** Jetpack Compose (Material 3, clean dark palette `#000000` / `#101216`)
- **System APIs:** `WindowManager` (`TYPE_APPLICATION_OVERLAY` / `TYPE_ACCESSIBILITY_OVERLAY`), `ForegroundService` (`specialUse` for Android 14/15), `AccessibilityService`, `TileService`.

---

## Permissions Used

| Permission | Purpose |
|---|---|
| `SYSTEM_ALERT_WINDOW` | Rendering protective dimming masks and the Blackout screen over other apps. |
| `BIND_ACCESSIBILITY_SERVICE` | Applying filters over the system status bar on Android 12+ and detecting the foreground package for auto-activating presets (without reading screen content: `canRetrieveWindowContent="false"`). |
| `FOREGROUND_SERVICE_SPECIAL_USE` | Keeping the protection service active in the background without being terminated by the system. |

---

## Build & Installation

1. Download the pre-built `.apk` from the **[Releases](../../releases)** section or clone the repository:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/OLED-Guard.git](https://github.com/YOUR_USERNAME/OLED-Guard.git)
2. Open the project in Android Studio and build/run it on a device running Android 8.0 (API 26) or higher.
