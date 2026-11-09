# Android AI Image Lab

A privacy-first Android image-editing app, initially targeted at the **Samsung Galaxy F17 5G (Exynos 1330, Mali-G68, 8 GB RAM)**.

## Product rules

- **On-device only:** selected photos are processed locally. No image upload or cloud inference.
- **No app-managed image storage:** the first version reads a photo through Android's system Photo Picker and keeps the result in memory. Export/save will happen only when the user explicitly chooses Android's system save/share flow.
- **No network permission:** the app manifest intentionally does not request `INTERNET`.
- **Consent-based editing:** support ordinary, non-explicit transformations only. Do not build undressing, nudification, or sexualized edits of real people.

## Current status

This is the initial Android Studio project scaffold. The photo-picker UI and local preview are implemented; the generative model runtime is **not yet integrated**. No AI generation or APK build is claimed at this stage.

## Build

1. Open this repository in a recent Android Studio.
2. Allow Gradle sync to complete.
3. Run the `app` configuration on an Android device.

The project uses Kotlin, Jetpack Compose, Android Photo Picker, min SDK 26, and Java 17.

## Device strategy

Start with 512-pixel SD 1.5-class workflows and measure memory use and latency on the actual F17. Do not assume Mali GPU acceleration is available until the chosen inference runtime is verified on this chipset. SDXL is out of scope for the first device build.

## Privacy checklist

- No `INTERNET` permission.
- No analytics or crash-reporting SDK.
- No image upload endpoint.
- No persistent image cache or database.
- Photo access is initiated by the user through the system picker.
