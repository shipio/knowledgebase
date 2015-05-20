/*
Title: Running iOS Instruments Tests
Sort: 1
*/

Instruments is an application that ships with Xcode to assist with performance, analysis and testing. Instruments also allows you to write and record scripts and tests that interact with your application's UI. To learn more about automation UI tests with Instruments, read [this article](http://developer.apple.com/library/mac/#documentation/DeveloperTools/Conceptual/InstrumentsUserGuide/UsingtheAutomationInstrument/UsingtheAutomationInstrument.html#//apple_ref/doc/uid/TP40004652-CH20-SW1) from Apple's Developer documentation.

Ship.io supports the execution of Instruments (or UI Automation) tests as part of your build process. During the execution of a Job, if a failing test is encountered the build will fail. When a build completes (pass or fail), the output of executed tests is available for download and review as well as a video recording of the tests executing on an iOS simulator.

1. To configure a Job to run Instruments tests, start by selecting "Add build step" and click "Run Instruments Tests".
2. In the "Run Instruments Tests" popup, select the Project and Target that contain your application.
3. In the "Simulators" tab, choose at least one simulated device to test against. On the "Test Selection" tab, select the Javascript file that contains your Instruments test and click "Save".
4. Now, review your build step, and create your job. That's all there is to it!
5. When your build finishes, click the "Log.txt" link in the Test Runs section of the Build Details page to download and view the output of your tests. 
