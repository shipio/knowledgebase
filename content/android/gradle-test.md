/*
Title: Using Gradle to Test an Android Project on the Emulator
Sort: 1
*/

Ship.io supports running your [Gradle](http://www.gradle.org/) tests on the Android emulator.

1. To get started using Gradle, create a new job and tie it to a repository containing an Android Gradle project (create a new job with GitHub).
2. Once the repository scan has completed, click "Add build step".
3. Click "Test An Android Gradle Project on Emulator" in the drop down list.
4. When the modal appears, choose your Gradle project and Gradle test task.
5. Click the "Emulator Configuration" tab at the top of the modal and configure the settings of the emulator (Android target version, CPU, skin, RAM).
6. Click "ok" and click "Create Job". Your new job should start automatically!
