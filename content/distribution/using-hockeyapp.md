/*
Title: Using HockeyApp
Sort: 2
*/

HockeyApp is a popular tool that helps developers distribute new versions of their iOS and Android applications to beta testers. Ship.io is tightly integrated with HockeyApp, making distribution even easier by automating the build process, code signing, and uploading of applications.

####Connecting the HockeyApp Add-On

You can connect or disconnect your HockeyApp account at any time by clicking "Add Ons" from the drop down menu. To connect your account, start by entering your API token and clicking "Connect". You can create your HockeyApp API token on HockeyApp by selecting API Tokens from the drop down menu. Ship.io requires an API Token with "Full Access" rights to the Apps you would like to upload to.

####Automating HockeyApp Uploads

Once you have your HockeyApp account connected to Ship.io you can configure your builds to automatically upload new versions of your application to HockeyApp. To configure a Build iOS Project or Build iOS Workspace build step to automatically upload your application, start by selecting the HockeyApp tab.

From here, check "Deploy this build to HockeyApp" and you may optionally specify the Application you'd like to upload to. If you don't specify an Application, HockeyApp will select one based on your bundle identifier or create a new one the first time your application is uploaded.

It is important to note that iOS applications can only be uploaded to HockeyApp if you have configured Code Signing. To learn more about Code Signing on Ship.io, see this Dev Center article.

####AdHoc HockeyApp Uploads

At times it can be useful to upload your application to HockeyApp manually, rather than having it upload as part of an automated build process.

1. To upload a specific build of your application, start by selecting "STATS" from the Dashboard.
2. On the Stats page, in the Build History tab, click on the build of your application you'd like to send to HockeyApp.
3. From here, click the "Upload to HockeyApp" link in the HockeyApp column in the Artifacts section.
4. Configure the options you'd like to use for the HockeyApp upload and click "Send". That's all there is to it!
