/*
Title: Using CocoaPods
Sort: 1
*/

We strongly recommend using [CocoaPods](http://cocoapods.org) for managing your application dependencies. CocoaPods will make for a better development experience than a dependency management solution that uses submodules and it is well suited for CI environments like Ship.io.

To compile applications that use CocoaPods for dependency management you must use an Xcode Workspace. To learn more about using Xcode Workspaces withship.ioo, and see an example using CocoaPods, check out the Build an iOS Workspace article.

Ship.io will use the version of CocoaPods specified in your `Podfile.lock`. We support a number of CoocaPods versions. To see the full list of CocoaPods versions that we have installed, see the [Build Environment](%base_url%/environment/build-environment#cocoapods) documentation.
 
We support CocoaPods server side. You do not need to check in your Pods directory. Simply check in the Podfile and we can take it from there. To enable CocoaPods installation, create a build step or edit an existing build step, go to the Build Settings tab, and check the Podfile that you'd like to install.
 
####Selecting Your Podfile

By default, Ship.io will detect and install any file named "Podfile". However, if your Podfile is named differently, we allow you to select another file to install. To do so, edit your build step and navigate to the "Build Options" tab.

Select the Podfile you wish to install, and click "OK". Next time you run your build, Ship.io will install the correct Podfile.

####Using Private CocoaPods
Ship.io has full support for authenticating private CocoaPods via SSH. All private Pods must use an SSH clone URL in their podspec (not HTTPS). To get started, add your SSH key to Ship.io. Once you have your SSH key added to your Ship.io account, edit your Build Step and navigate to the Build Options tab (shown above).

Within the Build Options tab, select the SSH key you would like to use to authenticate your private Pods. 

Click "OK", and the next time your build runs, your pod install should be authenticated with your SSH key.
