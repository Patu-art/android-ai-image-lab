# Android AI Image Lab

An Android photo-effects app targeted at the Samsung Galaxy F17 5G. The app shell runs on the phone; AI editing is provided online through Puter.js.

## Current implementation

- Mobile-first photo upload and preview.
- Effect presets and a custom edit prompt.
- Image-to-image generation through Puter.js.
- The app dynamically lists only image models whose IDs are marked with the provider's `:free` variant. If none are available, it refuses to fall back to a paid model.
- Result preview and save/open actions.
- No app-owned image gallery, database, or automatic permanent save.

## Important: free usage is not guaranteed

Puter.js uses a user-pays model. Accounts have a free monthly allowance, and some providers expose `:free` model variants with provider-controlled daily quotas. Availability, quotas, and model IDs can change or disappear. The app intentionally filters for `:free` image models and will not silently select a paid model. If the provider's free allowance is exhausted or no free image model supports editing, generation may be unavailable until the quota resets or a free model returns.

Puter documentation:
- Image-to-image API and input image support: https://docs.puter.com/AI/txt2img/
- Free model variants and quotas: https://docs.puter.com/AI/listModels/
- Usage limits and monthly free allowance: https://docs.puter.com/rate-limits-and-quotas/

## Data and privacy

- The app requests internet access because AI editing is online.
- When you generate, the selected photo and prompt are sent to Puter and the chosen upstream AI provider.
- Puter.js may upload larger image inputs to a temporary Puter file during processing, then deletes that temporary file after the call. The provider may have its own processing/retention terms.
- The app does not automatically save originals or results to an app-managed gallery or database.
- Choose only photos you have permission to upload. Do not upload sensitive images unless you have reviewed the provider's terms.
- The app is for non-explicit edits only. It does not implement undressing, nudification, or sexualized transformations of real people.

## Build

1. Open the repository in Android Studio.
2. Sync Gradle.
3. Run the `app` configuration on an Android device.
4. Sign in to Puter when prompted, then select an available free image model.

The Android app uses a WebView to render the bundled local interface. The Puter.js SDK is loaded from its official CDN at runtime. Android Photo Picker provides image access without broad storage permissions.

## Status

Source files have been added, but this repository update has not been compiled or run on a Galaxy F17. Treat it as an implementation draft until Gradle sync, Android build, sign-in, model discovery, image editing, and result saving are tested on-device.
