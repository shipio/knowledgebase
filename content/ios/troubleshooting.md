/*
Sort: 3
*/
###No Schemes Detected
You may come across an issue where your iOS schemes are not detected by Ship.io. This issue typically appears when there are no iOS workspaces present. Ship.io only supports iOS workspaces and iOS projects within workspaces. If you only have an iOS project, Ship.io will not be able to detect your schemes. Fortunately, this is an easy fix.

1. Open up Xcode. Create a new Workspace by going to File -> New -> Workspace or by pressing Control-Command-N.
2. With your new workspace open, drag your .xcodeproj file from Finder into your workspace project navigator.
3. Save your new workspace.
