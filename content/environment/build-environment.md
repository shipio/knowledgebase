/*
Sort: 0
*/

###Base Environment

Our base build image runs Mac OS X 10.10.3 Yosemite. All builds take place as the `administrator` user, which has full administrator access. Builds on Ship.io are transactional, which means that the system is completely rolled back to a clean state after every single build. You are free to make any changes to the build system that are necessary for your app to build, test, and deploy. If you require additional configuration of your build environment, please let us know ([send us an email](mailto:support@ship.io)), and we'll do our best to help you out.

Here are the specifications for the relevant software that we have installed.

- **Mac OS X version** `10.10.3 Yosemite`, build `14D136`.
- **Git version** `2.3.1`
- **Java build** `1.8.0_45`
- **Ruby version** `2.0.0-p481`

Ship.io allows you to execute shell scripts. Here are the shells that we support:

- **GNU** bash version `3.2.57`
- **ksh** version `ksh93u`
- **tcsh** version `6.17.00`
- **zsh** version `5.0.5`
- **tclsh** version `8.5`
- **Ruby** version `2.0.0-p481`
- **Python** version `2.7.6`
- **Perl** version `v5.18.2`

###iOS

####Xcode

We support Xcode `6.3.1` and `6.4 beta`. These applications are installed separately on the build environment, and the proper application is invoked according to your build settings.

We invoke Xcode from the command line using [xctool](https://github.com/facebook/xctool). We are currently using xctool version `0.2.1`.

Here is the exact xctool command that we run:

```
xctool -scheme scheme-name -sdk (iphoneos/iphonesimulator) -workspace workspace-path clean (build/build-tests) CONFIGURATION_BUILD_DIR="artifacts-directory" OBJROOT="artifacts-directory" SYMROOT="artifacts-directory" DSTROOT="artifacts-directory" CODE_SIGN_IDENTITY="certificate-name"
```

####CocoaPods

We have the following versions of CocoaPods installed: `0.37.0.beta.1`, `0.37.0.rc.1`, `0.37.0.rc.2`, `0.37.0`, `0.37.1`, `0.36.4`, `0.36.3`, `0.36.2`, `0.36.1`, `0.36.0.rc.1`, `0.36.0.beta.2`, `0.36.0.beta.1`, `0.36.0`, `0.35.0.rc2`, `0.35.0.rc1`, `0.35.0`, `0.34.4`, `0.34.2`, `0.34.1`, `0.34.0.rc2`, `0.34.0.rc1`, `0.34.0`, `0.33.1`, `0.33.0`, `0.32.1`, `0.32.0`, `0.31.1`, `0.31.0`, `0.30.0`, `0.29.0`, `0.28.0`, `0.27.1`, `0.27.0`

###Environment Variables

Ship.io sets a number of environment variables on our build environment. You can use our command line tool, shiptool, to set your own variables that will persist across build steps.

Name | Value
-----|------
SHIPIO | 1
CI | 1
JOB_ID | *Ship.io Job ID*
BUILD_NUMBER | *Incremental Ship.io build number*
REPOSITORY | *URL to Git repository*
BRANCH | *Branch of Git repository*
ARTIFACTS_DIRECTORY | *Path to build artifacts directory*
JAVA8_HOME | *Path to Java 8*
JAVA7_HOME | *Path to Java 7*
ANDROID_HOME | *Path to Android SDK*
ANDROID_NDK_HOME | *Path to Android NDK*
TMPDIR | *Path to temporary directory where all builds are run*
 
`ARTIFACTS_DIRECTORY` is a path relative to the current working directory (`pwd`), and is 16 randomly generated characters. It is created when Build Project step is run. The `ARTIFACTS_DIRECTORY` should be considered read-only, as the artifacts are uploaded at the end of the Build Project step.
 
These variables are accessible in iOS compile, iOS test run (both unit and instrument), as well as in Android compile and unit test run.
