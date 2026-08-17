
# Liquid Galaxy LAB App Store

This repository contains data for the Liquid Galaxy LAB App Store. It is designed to store data for various apps, including their APK files, images, and associated information.

## Repo Structure

The repository follows this structure:

```
apps/
  └── La_Palma/
       ├── 1.webp
       ├── 2.webp
       ├── 3.webp
       └── app/
           └── La Palma Volcano Tracking Tool_1.0.0.apk
  └── SatNOGS/
       ├── 1.webp
       ├── 2.webp
       ├── 3.webp
       └── app/
           └── SatNOGS Visualization Tool_1.0.5.apk
  └── other_app_folders/
store.json
```

## How to Contribute

1. **Manual App Addition**
   - Apps from APKPure need to be manually added to the repository.
   - Each app should have its own folder under `apps/`. The folder structure should look like:

     ```
     apps/
       └── <app_name>/
            ├── <image_files>.webp
            └── app/
                └── <app_name>_<version>.apk
     ```

2. **Adding Images**
   - All images should be converted to **WebP** format to ensure optimal storage and performance.
   - The app icon must be a **square shape**, ideally 512x512 pixels.
   - All carousel images must be of the **same size** (consistent dimensions).
   - Rename the carousel images sequentially as `1.webp`, `2.webp`, `3.webp`, etc.
   - Only high-quality photos should be included.

3. **Adding Data to `store.json`**
   - Add an entry for the app in `store.json`. Follow this structure:

     ```json
     {
         "name": "<app_name>",
         "icon": "<icon_image>.webp",
         "category": "<category>",
         "carousel_assets": [
             "<image_1>.webp",
             "<image_2>.webp",
             ...
         ],
         "base_url": "/apps/<app_name>/",
         "file": "app/<app_name>_<version>.apk",
         "pwa_link": "",
         "type": "app",
         "date": "<release_date>",
         "android_OS": "<android_version>",
         "version": "<version>",
         "content": "<detailed_app_description>"
     }
     ```

   - App name should follow the 32 character limit.
   - Be sure to properly format the app description with `/n` for new lines.
   - Categories can be the following:
      - Education
      - Tools
      - Maps & Navigation
      - Travel & Local
      - Auto & Vehicles
      - Arcade
      - Strategy
      - Social

4. **Submission Methods**
   - **Pull Requests (PR):** You can directly submit your application by making a PR. You may use tools like Antigravity to help you. Each PR should contain **one APK file**, **one set of images**, and **the corresponding JSON entry**. Ensure that all images are converted and renamed before submitting.
   - **Google Drive:** Alternatively, organize your content in a Google Drive folder (the same root directory used for your GSoC project). Include the APK, images, and JSON data, so mentors can help add it to the Go Web Store.

5. **Review Process**
   - Each PR will be reviewed before being merged. Contributors should ensure that all files are named correctly, formatted properly, and meet the repository's standards.

## Example App Entry in `store.json`

Here is an example of how an app entry should look in the `store.json` file:

```json
{
    "name": "La Palma VolTrac",
    "icon": "icon.webp",
    "category": "Education",
    "carousel_assets": [
        "1.webp",
        "2.webp",
        "3.webp",
        "4.webp",
        "5.webp",
        "6.webp",
        "7.webp",
        "8.webp"
    ],
    "base_url": "/apps/La_Palma_VolTrac/",
    "file": "app/La Palma Volcano Tracking Tool_1.0.0.apk",
    "pwa_link": "",
    "type": "app",
    "date": "Dec 29, 2022",
    "android_OS": "6.0+",
    "version": "1.0.0",
    "content": "Volcanic Activities of La Palma visualized onto the Liquid Galaxy.
La Palma Volcano Eruption Tracking Tool is an app built on the Flutter framework that allows the Visualization of various Tracks..."
}
```

## Important Notes

- Changes should only be made **one at a time**. This means that for each pull request, you should include one APK, one set of images, and one JSON data entry.
- Ensure that the `store.json` file remains properly formatted and doesn’t contain any errors.
- Make sure all APK files are ideally **under 50 MB**. While GitHub allows up to 100 MB, larger files usually indicate unoptimized assets or debug builds. Ensure you submit a **release build**. Consider splitting the package if necessary.

## APK Size Optimization

If your APK is larger than expected, here are some ways to reduce the build size without changing the app's core functionality.

### Code Shrinking & Obfuscation (R8/ProGuard)

Add `isMinifyEnabled = true` to `build.gradle.kts`.

The Android R8 compiler analyzes your code to determine which classes and methods are actually used. It can then remove unused code ("dead code"). As a bonus, it can obfuscate the remaining code by renaming long class and method names to shorter ones, saving additional bytes.

### Resource Shrinking

Add `isShrinkResources = true` to `build.gradle.kts`.

Code shrinking removes unused code, but images, layouts, and XML files associated with that code may also become unnecessary. Resource shrinking works together with R8 to identify and remove unused resources such as `.xml`, `.png`, and `.webp` files that are no longer referenced by the remaining application code.

### ABI Splitting (Application Binary Interface)

Use the following command instead of the standard Flutter APK build command:

```bash
flutter build apk --split-per-abi
```

Android devices use different CPU architectures, primarily `arm64-v8a`, `armeabi-v7a`, and `x86_64`. A standard APK can bundle the Flutter engine binaries for multiple architectures into a single, larger "fat" APK.

By splitting the APK, you generate a separate APK for each supported architecture, allowing users to download only the binary required by their device.

> **Note:** `arm64-v8a` is the modern standard for most phones and tablets, while `x86_64` is commonly used by Android emulators and some Chromebooks. Prefer a standard build when APK size is not a major constraint or when broader architecture support is important. Use ABI splitting when minimizing APK size is a priority.

### Use WebP Images Instead of PNGs/JPGs

WebP provides efficient lossless and lossy compression. Converting images to WebP can significantly reduce file size while maintaining comparable visual quality. Depending on the image and compression settings, WebP images can often be substantially smaller than equivalent PNG or JPG files.

These are some simple ways to reduce APK size without changing the app's core functionality.

I hope this helps anyone dealing with bloated build sizes!

## Thank You for Contributing

Your contributions help the Liquid Galaxy LAB community. We appreciate your efforts to keep the app store up to date with new apps and content.
