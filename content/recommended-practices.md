/*
Sort: 1
*/

Setting up a build environment can be a time consuming and tricky process. Here at Ship.io, we abstract this complexity away so that developers don't have to worry about those details. That means that our build environments have been designed to support the widest range of mobile application configurations while also ensuring all of our users' data is handled securely. Achieving these goals means that some things which are possible in a dedicated server environment are not supported on Ship.io. 

Here is a short list of recommendations that will help your team get the most value out of Ship.io:

- **Git Submodules**: Ship.io has no problem pulling git submodules. However, it's important that our system have access to pull them at build time. While we can automatically configure access to your git repository you may need to manually configure access to any private submodules that your project uses.

- **3rd Party Frameworks/Libraries**: It's important to include any 3rd party libraries or frameworks in your source code repository so that they are accessible during the build process. For Open Source frameworks this can usually be accomplished with the use of Git Submodule's.
Unsupported Test Frameworks: Please see the above list of supported Unit Test frameworks. Test projects developed using other frameworks will not run correctly on Ship.io.

- **Shell Scripts**: We support the execution of custom shell scripts with Xcode post build scripts. You have full administrator access to the build server while your build is running, so feel free to make any necessary environment changes.  We also support Shell scripts now as a separate build step.  We run build steps in order so you can include a shell script step after the build, etc.

- **iOS SDK Version**: When creating an iOS job, be sure to select the correct SDK version. Some projects require that they be built again the device SDK. When creating or editing your job look for the option titled iOS SDK to modify this setting. 
