/*
Title: Building an iOS Workspace
Sort: 0
*/

This walk through is targeted at developers that would like to setup a Job that compiles an Xcode iOS workspace. This includes workspaces that make use of the CocoaPods dependency management framework. **You must use workspaces, not solo projects, with Ship.io.**

1. From the Ship.io dashboard, click "New Job".
2. Find the repository that contains your iOS workspace and click "Create Job".
3. Now, add a build step for building your iOS workspace.
4. Click "select a workspace" in the "Project Configuration" tab. Then pick the workspace and scheme you would like to build. You can also configure Code Signing, HockeyApp uploads, and TestFlight uploads from here.
5. If you're using CocoaPods you can select which Pods you'd like to install from the Build Options tab.
6. Review your build step, and create your job. That's it!
