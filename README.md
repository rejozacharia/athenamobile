# Athena College Mobile App

This is the official mobile application for Athena College ([www.athena.college](https://www.athena.college)), customized specifically for our students and staff.

It is based on the official [Moodle Mobile App](https://github.com/moodlehq/moodleapp) (version 5.0.0), providing access to Moodle courses and activities on the go.

## Key Features (from Moodle Mobile)

*   Access course materials offline.
*   Receive instant notifications for messages and events.
*   Find and contact other people in your courses.
*   Participate in forum discussions.
*   View calendar events.
*   Submit assignments.
*   Track learning progress.
*   ...and much more!

## Athena College Customizations

This version includes the following customizations:

*   **App Branding:** Renamed the app to "Athena College" and updated the app icon and splash screen to use the Athena College logo.
*   **Site Configuration:** The app is configured to connect exclusively to `https://www.athena.college`.
*   **Color Theme:** Updated the visual theme to match Athena College's branding (Orange primary, Gold accent, White background).
*   **App ID:** Set to `college.athena.mobileapp`.

## Development Setup

To set up the development environment for this project, you will need:

1.  **Node.js:** Version `v20.18.0` or higher, but less than `v21`. We recommend using a Node Version Manager (like [NVM](https://github.com/nvm-sh/nvm) or [NVM-Windows](https://github.com/coreybutler/nvm-windows)) to manage versions.
    *   `nvm install 20.18.0`
    *   `nvm use 20.18.0`
2.  **Java Development Kit (JDK):** Version **17**. Ensure `JAVA_HOME` environment variable is set correctly and the JDK 17 `bin` directory is prioritized in your system `PATH`.
3.  **Android Studio:** Install Android Studio and use the SDK Manager to install:
    *   Android SDK Platform for your target API level (e.g., API 34 or 35).
    *   Android SDK Build-Tools version **34.0.0**.
    *   Android SDK Platform-Tools.
    *   Android SDK Command-line Tools (latest).
    *   Android Emulator and create an Android Virtual Device (AVD).
4.  **Ionic CLI & Cordova:** Install globally using npm:
    *   `npm install -g @ionic/cli`
    *   `npm install -g cordova`
    *   `npm install -g native-run`
5.  **Git Bash (for Windows users):** Required to run certain build scripts.
6.  **Project Dependencies:** Navigate to the project directory (`moodleapp-custom`) and run:
    *   `npm install`
    *   `npm install --save-dev cross-env` (Installs cross-env if not already present)

## Building and Running

**Important for Windows Users:** Due to Cordova hook scripts written for Bash, it's recommended to run build and emulate commands using **Git Bash**.

1.  **Navigate to Project Directory:** Open Git Bash and `cd` into the `moodleapp-custom` directory.
2.  **Ensure Environment Variables are Loaded:** Make sure your `JAVA_HOME` and Android SDK paths (`%ANDROID_HOME%\platform-tools`, etc.) are accessible within your Git Bash session. You might need to add them to your `.bashrc` or `.bash_profile` for persistence, or export them temporarily:
    ```bash
    export JAVA_HOME="/c/Program Files/Java/jdk-17" # Adjust path as needed
    export ANDROID_HOME="/c/Users/YourUser/AppData/Local/Android/sdk" # Adjust path as needed
    export PATH="$PATH:$JAVA_HOME/bin:$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$ANDROID_HOME/cmdline-tools/latest/bin"
    ```
3.  **Generate Resources (if icons/splash changed):**
    ```bash
    ionic cordova resources android --force
    ```
4.  **Run on Emulator:**
    *   Start your Android Emulator (AVD).
    *   Run the emulate command, specifying the target if needed (e.g., `emulator-5554`):
        ```bash
        ionic cordova emulate android --target=emulator-5554
        ```
5.  **Build Release APK/AAB:**
    ```bash
    # For APK
    ionic cordova build android --release

    # For Android App Bundle (AAB - Recommended for Play Store)
    ionic cordova build android --release -- -- --packageType=bundle
    ```
    *Note: Release builds require signing.*

## License

[Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0)
