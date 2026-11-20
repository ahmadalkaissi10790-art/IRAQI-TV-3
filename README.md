# IRAQI TV (com.iraqitv.live)

Android TV app: Kotlin + Jetpack Compose, Arabic/RTL, dark theme, remote-first.
Playback = official YouTube IFrame Player API inside a WebView (no URL extraction, no proxying).

## Build without Android Studio
1. Create a GitHub repo, upload this folder, push to `main`.
2. GitHub > Actions > "Build IRAQI TV APK" (runs automatically).
3. Download the `iraqi-tv-debug-apk` artifact, install on the TV (adb or a file manager / Send Files to TV).

## Adding a verified channel
Edit `app/src/main/assets/channels.json`. Fill ONLY what you have verified yourself:
- `youtubeUrl`  : the official channel page
- `liveVideoId` : the 11-char ID of the current official live broadcast (…/watch?v=ID), OR
- `liveChannelId` : the channel's UC… ID (uses YouTube's official live_stream embed, survives restarts of the stream)
- `lastVerified` : e.g. "2026-11-20"
A channel with neither ID stays visible but marked "غير متاح" and cannot be opened.
Note: some broadcasters disable embedding; those will show the in-app error screen.
Optional: drop an updated `channels.json` into the app's files dir to update the catalog without rebuilding.

## Remote control
Player: Left/Channel+ = next, Right/Channel- = previous, OK = show info / pause / retry on error, Back = list.
Home: long-press OK on a card = add/remove favorite.
