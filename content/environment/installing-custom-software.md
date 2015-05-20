/*
Sort: 1
*/

If your app's build and test requires a piece of software that is not pre-installed on our builders, there is an easy way for you to get it installed.

When you are configuring a Job, set the up the first Build Step as a Shell Script. From here you can write a Bash script where you can customize the build environment. This is how you can install any required software.

Our builder machines are running OSX, and you have Administrator privileges, so you can use [Homebrew](http://brew.sh/) to install many packages. If Homebrew does not offer it, you can put the install steps in a Shell Script and it will be available by the time your build and test phases start.
