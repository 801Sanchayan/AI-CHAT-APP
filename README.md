# Offline Android AI Chat App

A minimal Android app built with Kotlin + Jetpack Compose that works fully offline.

## Features
- Local chat UI
- No network permissions required
- Simple on-device rule-based assistant (`localReply`)
- Easy extension point for a real on-device LLM

## Run
1. Open this folder in Android Studio (Ladybug or newer).
2. Let Gradle sync.
3. Run `app` on an emulator/device.

## Upgrade to real offline AI
Replace `localReply()` in `ChatViewModel` with an on-device inference library such as:
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

## Upload to GitHub (step-by-step)
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
```

## Turn placeholder replies into real offline AI
Replace `localReply()` in `app/src/main/java/com/example/offlineaichat/MainActivity.kt` with an on-device inference implementation, such as:
- MediaPipe LLM Inference
- llama.cpp Android bindings
- ONNX Runtime Mobile

Then load a local quantized model from app storage/assets and stream tokens into the chat.
