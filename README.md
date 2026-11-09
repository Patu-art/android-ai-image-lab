# Android AI Image Lab

An Android photo-effects app targeted at the Samsung Galaxy F17 5G. The app interface runs on the phone; image editing is provided online through Puter.js.

## Current implementation

- Mobile-first photo upload and preview.
- Effect presets and a custom edit prompt.
- Image-to-image editing through Puter.js `puter.ai.txt2img()` with an input image.
- Puter account sign-in; no developer API key is embedded in the app.
- Result preview and explicit save/open actions.
- No app-owned image gallery, database, or automatic permanent save.

## Free usage: important limitation

Puter documents a **free monthly allowance** for each user account, not a guaranteed daily number of image generations. Image models may consume that allowance at different rates. If the allowance is exhausted, Puter prompts the user to upgrade. The app does not promise unlimited free generation, cannot reset provider quotas, and does not silently choose another model to bypass limits. Do not upgrade if you want to keep usage free.

Official documentation:
- Image-to-image API: https://docs.puter.com/AI/txt2img/
- User-Pays Model and free monthly allowance: https://docs.puter.com/user-pays-model/
- Model listing API: https://docs.puter.com/AI/listModels/ (this lists chat/completion models, not image models)

## Data and privacy

- The app requests internet access because AI editing is online.
- When you generate, the selected photo and prompt are sent to Puter and the selected upstream AI provider.
- Puter.js documents that a Blob/File or data URI larger than 1 MiB may be uploaded to a temporary file in the user's Puter storage and deleted after the request, whether it succeeds or fails. This temporary upload still means data is transmitted and temporarily stored outside the phone.
- The provider may have its own processing and retention terms. Review them before uploading sensitive photos.
- The app does not automatically save originals or results to an app-managed gallery or database.
- Choose only photos you have permission to upload. This app supports non-explicit transformations only; it does not implement undressing, nudification, or sexualized transformations of real people.

## Build

1. Open the repository in Android Studio.
2. Sync Gradle.
3. Run the `app` configuration on an Android device.
4. Connect/sign in to a Puter account and use its free monthly allowance. Stop when the allowance is exhausted if you do not want to pay.

The Android app uses a WebView to render the bundled local interface. The Puter.js SDK is loaded from its official CDN at runtime. Android Photo Picker provides image access without broad storage permissions.

## Status

Source files have been added, but this repository update has not been compiled or run on a Galaxy F17. Treat it as an implementation draft until Gradle sync, Android build, sign-in, image editing, and result saving are tested on-device.
