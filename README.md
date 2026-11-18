# NOVA AI Mobile

A native Android (Kotlin + Jetpack Compose) offline-first chat app prototype.

## Current status

- Purple futuristic chat UI
- Local chat interaction
- No network permission and no API key
- Local model runtime interface (`LocalModelEngine`)
- Demo response engine works offline

**Important:** This first app build does NOT yet run the trained NOVA PyTorch `.pth` model. The `.pth` checkpoint from Colab is not directly compatible with Android. The current engine is explicitly a demo. The next integration step is to export a compatible model (for example ONNX) and implement an Android inference engine.

## Build APK from an Android phone

This project includes a GitHub Actions workflow so you do not need Android Studio on your phone.

1. Create a GitHub repository named `NOVA_AI_Mobile`.
2. Upload the contents of this ZIP to the repository (not the ZIP file itself).
3. Open the repository on GitHub.
4. Go to **Actions** and enable workflows if asked.
5. Select **Build NOVA Android APK** and tap **Run workflow**.
6. Wait for the workflow to finish.
7. Open the completed run, find **Artifacts**, and download `NOVA-AI-debug-apk`.
8. Extract the artifact ZIP to get `app-debug.apk`.
9. Open the APK on your phone and install it. Android may ask you to allow installation from your browser/file manager.

## Build locally

Requires JDK 17 and Android SDK platform 35:
```bash
gradle assembleDebug
```
APK output:
`app/build/outputs/apk/debug/app-debug.apk`

## Project structure

- `app/src/main/java/com/novaai/mobile/MainActivity.kt` — Compose UI
- `LocalModelEngine.kt` — model runtime interface and demo engine
- `.github/workflows/build-apk.yml` — cloud APK build workflow

## Next engineering milestone

1. Export a small NOVA model to ONNX or another Android-compatible runtime.
2. Implement tokenizer parity between training and Android.
3. Add model download/import and storage management.
4. Replace `DemoLocalEngine` with real local inference.
5. Test speed and memory usage on the target Android device.
