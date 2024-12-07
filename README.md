
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
   - Rename the images sequentially as `1.webp`, `2.webp`, `3.webp`, etc.
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
         "base_url": "./apps/<app_name>/",
         "file": "/app/<app_name>_<version>.apk",
         "pwa_link": "",
         "type": "app",
         "date": "<release_date>",
         "android_OS": "<android_version>",
         "version": "<version>",
         "content": "<detailed_app_description>"
     }
     ```
   - Be sure to properly format the app description with `/n` for new lines.

4. **Pull Requests**
   - All changes should be made via **Pull Requests (PR)**.
   - Each PR should contain **one APK file**, **one set of images**, and **the corresponding JSON entry**.
   - Ensure that all images are converted and renamed before submitting the PR.

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
    "file": "/app/La Palma Volcano Tracking Tool_1.0.0.apk",
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
- Make sure all APK files are within the size limits (below 100 MB), as larger files will not be accepted by GitHub.

## Thank You for Contributing!

Your contributions help the Liquid Galaxy LAB community. We appreciate your efforts to keep the app store up to date with new apps and content.
