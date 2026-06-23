# Offline Android AI Chat App

A minimal Android app built with Kotlin + Jetpack Compose that works fully offline.

## What this app does
- Local chat UI (no backend).
- No network permission in `AndroidManifest.xml`.
- Offline placeholder assistant via `localReply()` in `ChatViewModel`.
- Clean extension point to swap in a real on-device LLM.

## Quick start (ready-to-run)
1. Install **Android Studio** (latest stable) with Android SDK 34.
2. Install **JDK 17** (recommended for Android Gradle Plugin compatibility).
3. Open this project folder in Android Studio.
4. Let Android Studio sync and auto-download Gradle dependencies.
5. Run the `app` module on an emulator/device.

> If you want CLI builds, generate Gradle wrapper first (on a machine with internet):
>
> ```bash
> gradle wrapper --gradle-version 8.7
> ./gradlew :app:assembleDebug
> ```

## Deploy / download an APK from GitHub Actions
This repo includes a GitHub Actions workflow at `.github/workflows/android-apk.yml` that builds a debug APK automatically.

### One-time GitHub upload
Run these commands in your terminal from the project root:

```bash
git init
git add .
git commit -m "Initial commit: offline Android AI chat app"

git branch -M main
git remote add origin https://github.com/<YOUR_USERNAME>/<YOUR_REPO>.git
git push -u origin main
```

If the remote already exists, update it with:

```bash
git remote set-url origin https://github.com/<YOUR_USERNAME>/<YOUR_REPO>.git
git push -u origin main
```

### Build and download the APK
1. Open your repository on GitHub.
2. Go to **Actions**.
3. Select **Build Android APK**.
4. Click the latest successful run.
5. Download the `offline-ai-chat-debug-apk` artifact.
6. Install `app-debug.apk` on an Android device after enabling installs from unknown sources.

### Manual deploy build
You can also run the workflow manually from **Actions → Build Android APK → Run workflow**.

> Note: The workflow creates a debug APK for easy testing. Publishing to Google Play requires a signed release build and Play Console credentials.

## Turn placeholder replies into real offline AI
Replace `localReply()` in `app/src/main/java/com/example/offlineaichat/MainActivity.kt` with an on-device inference implementation, such as:
- MediaPipe LLM Inference
- llama.cpp Android bindings
- ONNX Runtime Mobile

Then:
1. Place your quantized model in assets or app-private storage.
2. Run inference on a background coroutine/thread.
3. Stream partial tokens into the UI for real-time chat updates.

## Current project structure
- `app/src/main/java/com/example/offlineaichat/MainActivity.kt` — UI + ViewModel + local responder
- `app/build.gradle.kts` — Android/Compose config
- `.github/workflows/android-apk.yml` — automated APK build artifact
- `settings.gradle.kts`, `build.gradle.kts`, `gradle.properties` — root Gradle config
