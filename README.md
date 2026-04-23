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
- MediaPipe LLM Inference
- llama.cpp Android bindings
- ONNX Runtime Mobile

Then load a local quantized model from app storage/assets and stream tokens into the chat.
