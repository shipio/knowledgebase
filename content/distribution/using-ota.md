/*
Title: Using Ship.io OTA
Sort: 3
*/

Ship.io offers a convenient built-in OTA system for distributing your latest builds to beta testers. Whenever a new build of your application is finished an email is sent that contains a link to your application. When the recipient taps the link on a mobile device they will be prompted to install the application.

Note that OTA for IOS only works for applications that have Code Signing properly configured. It is also important that the device be configured ahead of time with any necessary Provisioning Profiles.

Android applications require no extra configuration. OTA notifications for Android only require a successfully built Android application.

When configuring a build step for your application, click the "OTA" tab and enter the email addresses you would like to receive OTA notifications.

You can also send an OTA e-mail for an app after a build completes. Just go to the Build Details page of the build and click the "Send OTA Notification" link for the app file in the Artifacts section of the page.
