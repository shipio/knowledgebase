/*
Sort: 3
*/
###APK install error: Package with that name and different signature already installed
This article explains how to fix the situation where an APK built by Ship.io fails to install on Android with the following message: "Package with that name and different signature already installed"

This usually happens because a build of the app has already been installed on the device, and that build was signed with a different keystore (for example, the default Android IDE keystore).

To solve this, you can upload the same keystore from your development machine to Ship.io on the [Code Signing](https://ship.io/code_signing) page and then choose it when you create the "Build an Android Project" build step. You can usually find the default keystore at `~/.android/debug.keystore`.

###Android/Gradle Project Not Detected
For Android projects, Ship.io scans for gradle tasks from your using your gradlew. Ship.io requires that your gradle wrapper and all config files be included in the repository, so that [we are always running the exact same gradle version that you are](http://www.gradle.org/docs/current/userguide/gradle_wrapper.html).

Sometimes .gitignores are set up to exclude the gradle files, and that means our system will not detect the project.

Please make sure that all of the files (`build.gradle`, `gradle.properties`, `gradlew`, `settings.gradle`, and the `gradle/` path) are in the repository.

If your Android project is still not being detected, please check out your repository into a fresh directory and run the gradlew command to see if it run successfully and that there are no other dependencies that are not being included. It is important to check out into a fresh directory to avoid any false positives due to paths or .gitignore'd files in the development environment.
