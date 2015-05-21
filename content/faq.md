/*
Title: Frequently Asked Questions
Sort: 0
*/

####How does Ship.io store my Developer Certificates and Provisioning Profiles?

Developer Certificates and Provisioning Profiles are used to sign iOS builds so that they can be installed on devices for testing. When uploaded to Ship.io we immediately encrypt the files, before they ever touch a disk, using a combination of 2048-bit RSA and 256-bit AES encryption and store them securely in an access-controlled repository. Once encrypted, the files can only be read by our build servers and are only ever decrypted long enough to sign the build, after which time they are immediately destroyed.

####How does Ship.io store my Android Keystore?

An Android keystore is used to sign your app so that it can be installed on devices for testing. When uploaded to Ship.io, we store it securely in an access-controlled repository. Our builder machine (which is behind a firewall) downloads it when needed for a build. The builder machine is destroyed after the build, so the keystore doesn't reside there for very long.

The Edit Job page contains a link to download the keystore on the build-step where it is attached. That download link is to a handler in the webapp which validates access before streaming the keystore data from the repository.

####What changes does Ship.io make to my repository?

In cases where your Github account has access to make changes to the repository we'll setup a [web hook](https://help.github.com/articles/post-receive-hooks), that's it.

####What does Ship.io do with my code?

Here at Ship.io we understand how important your code is and keeping it safe is our highest priority. When your code is pulled down to our servers to run a build the transmission is always encrypted. As soon as the build is complete, no matter success or failure, the code is immediately deleted. Finally, we'll never look at your code unless we're assisting you with a problem and you have specifically given us permission.

For more information see our [privacy policy](https://app.ship.io/privacy) and [terms of service](https://app.ship.io/terms_of_service).

####How does Ship.io sign Android APKs?

Similar to Apple's system, which uses Provisioning Profiles, Android requires that all application files (APK's) be signed with a keystore before they can be installed on a device. Keystore's come in two flavors:

- **Debug Keystores**: These keystores are used only for development. APK's signed with a Debug Keystore cannot be uploaded to Google Play and require that end users who install the application turn on the "Unknown Sources" setting [(see how)](http://www.youtube.com/watch?v=p8rnyuCsrTg).
- **Release Keystores**: These keystores are used to sign the production version of your application so that it can be uploaded and distributed on Google Play.

You can upload either keystore-type to Ship.io from the Code Signing page and choose the keystore when creating your build step. However, you can also choose to have Ship.io generate a debug keystore when creating your build step for simplicity (if you don't intend on publishing the generated app to the Google Play). Go to the [Android build step help page](http://support.ship.io/hc/en-us/articles/202290039-Using-Gradle-to-Build-an-Android-Project) for more details.

The important points to understand about signing Android applications are:

All applications must be signed. The system will not install an application on an emulator or a device if it is not signed.
To test and debug your application, the build tools sign your application with a special debug key that is created by the Android SDK build tools.
You can use self-signed certificates to sign your applications. No certificate authority is needed.
The system tests a signer certificate’s expiration date only at install time. If an application’s signer certificate expires after the application is installed, the application will continue to function normally.
You can use standard tools – Keytool and Jarsigner – to generate keys and sign your application .apk files.
After you sign your application for release, we recommend that you use the `zipalign` tool to optimize the final APK package.

####How do I make sure my project will build using Ship.io?

Setting up a build environment can be a time consuming and tricky process. Here at Ship.io, we abstract this complexity away so that developers don't have to worry about those details. That means that our build environments have been designed to support the widest range of mobile application configurations while also ensuring all of our users' data is handled securely. Achieving these goals means that some things which are possible in a dedicated server environment are not supported on Ship.io. Here is a short list of recommendations that will help your team get the most value out of Ship.io:

- **Git Submodules**: Ship.io has no problem pulling git submodules. However, it's important that our system have access to pull them at build time. While we can automatically configure access to your git repository you may need to manually configure access to any private submodules that your project uses.
- **3rd Party Frameworks/Libraries**: It's important to include any 3rd party libraries or frameworks in your source code repository so that they are accessible during the build process. For Open Source frameworks this can usually be accomplished with the use of Git Submodule's.
Unsupported Test Frameworks: Please see the above list of supported Unit Test frameworks. Test projects developed using other frameworks will not run correctly on Ship.io.
- **Shell Scripts**: When creating your job configuration, you can choose steps such as building the application, running tests, or even custom shell scripts.
- **iOS SDK Version**: When creating an iOS job, select the correct SDK version. Some projects require that they be built again the device SDK. When creating or editing your job look for the option titled iOS SDK to modify this setting.

If these limitations are a deal breaker for your organization please [contact us](mailto:team@ship.io) to discuss a dedicated server plan.

####How are builds triggered?

After creating a job, the job can be triggered to create a build in three ways.

- **Manually**: Clicking "Start Build" in Ship.io
- [**Commit Hooks**](%base_url%/source-control/automatically-triggered-builds#commit-hooks): We receive a POST notification from your git hosting service.
- [**Polling**](%base_url%/source-control/automatically-triggered-builds#polling): Ship.io will poll your repository every 10 minutes, and will trigger a build if changes are detected.

Setting up your Job with a schedule of Commit hooks is often the preferred method of triggering a build.

####How do I integrate Ship.io with my own backend or web service?

We support integration with 3rd party systems by sending Notification webhooks whenever a build completes. These hooks are sent as an HTTP POST request to a URL that you specify and contain information about the status of the build, the associated job, repository and links to download build artifacts. To learn more about setting up webhooks, see the [Webhooks](%base_url%/notifications/webhooks) documentation.
