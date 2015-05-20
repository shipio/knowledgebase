/*
Title: Code Signing and Provisioning
Sort: 2
*/

As you're probably aware, code signing and provisioning of iOS apps can be a bit of a challenging process to get right. It requires Developer Certificates and Provisioning Profiles and you must make sure they're used correctly when building your application. Fortunately, we automate the entire process for you so you can set it and forget it.

1. To allow Ship.io to codesign your application, you'll first need to upload your Developer Certificate and Provisioning Profile. Start by clicking "Code Signing" in the drop down menu.

2. Upload any Developer Certificates and Provisioning Profiles you'd like to use by selecting "Choose File". Once uploaded you can remove your files at any time clicking the red "X" next to the name.

    Your Developer Certificate must be in .p12 format, have a Private Key and cannot be password protected.

3. Now that you've uploaded your certificate and profile it's time to configure a Job to sign your application. If you're building an iOS Project or iOS Workspace simply edit your build step and click the "Code Signing" tab. From here, check "Sign this build" and select your Developer Certificate and Provisioning Profile from the drop downs.

    That's all there is to it! Now you're all set to sign and provision your applications using Ship.io.
