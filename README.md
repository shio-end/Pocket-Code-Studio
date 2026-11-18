# Pocket Code Studio (Android)

Mobile-first offline code editor for Android. This is an original app inspired by code editor workflows, **not Microsoft's official VS Code** and not an implementation of the desktop VS Code extension host.

## Features

- Editable file explorer, rename and delete
- Multiple tabs, syntax-colored editing, line numbers, extra coding keys
- Search and replace current file, basic indentation, automatic close brackets
- HTML/CSS/JavaScript preview + JavaScript console
- Persistent projects using WebView localStorage, dark/light themes
- Import local text files and .pocketcode.json backups
- Export individual file, .zip project, or full .pocketcode.json backup
- Offline operation, no server, Windows PC, or account needed for the installed app

## Use immediately on a phone

Open `app/src/main/assets/index.html` in a modern Android browser (or serve the file over localhost). The native Android version is preferable because file import/export and app storage are more reliable.

## Build APK without using a Windows PC

1. Create a GitHub repository from this folder, preserving `.github/workflows/build-apk.yml` and the `app/` subfolders. You can do this through GitHub in a mobile browser.
2. In GitHub, go to **Actions → Build Android APK → Run workflow** (or push to `main` to trigger it).
3. After the workflow succeeds, open the run, select **Artifacts → PocketCodeStudio-debug-APK**.
4. Unzip the downloaded artifact on Android and install `app-debug.apk` if your device allows installs from this source.

The debug APK is not signed for Play Store release. It is signed with Android's automatically generated **debug** key for device testing; production distribution needs a private release signing key and additional review.

## Build on a computer (optional)

Open this folder with Android Studio, or build with JDK 17, Android SDK 35, Gradle 8.11.1:

```sh
gradle assembleDebug
```

APK is located at `app/build/outputs/apk/debug/app-debug.apk`.

## Important limitations

- Run supports HTML, CSS, and JavaScript web pages only. Other languages can be edited but not executed.
- No VS Code marketplace extensions, Node.js, Python interpreter, true integrated terminal, debugger, or Git integration yet.
- The project is saved inside app-local WebView storage, *not* as an Android directory. Use Export ZIP or Export backup regularly. Clearing app data removes unsaved projects.
- The live preview is restricted to offline content; external network resources may not load.
- ZIP export is stored-only (uncompressed) for cross-platform compatibility.
