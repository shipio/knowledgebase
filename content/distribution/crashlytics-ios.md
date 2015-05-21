/*
Title: Using Crashlytics Beta with iOS
Sort: 0
*/

The [Crashlytics](https://try.crashlytics.com/) team has made it very easy to configure your iOS build to include the Crashlytics library.

This article assumes you already have an existing iOS Job set up in Ship.io that you want to add [Crashlytics Beta](http://try.crashlytics.com/beta/) support to.

First you'll need to get an account with [Fabric](https://get.fabric.io/) and follow their instructions for getting started.

As part of getting started in the registration process, you will need to add the Crashlytics library to your iOS project. Be sure to commit this change and push it onto the branch that Ship.io is using.

After that, go into Ship and edit the Build Steps for the Job you are adding Crashlytics to. You're going to be adding a new Build Step, "Run Shell Script". Crashlytics Beta deployment requires a .ipa file, so ensure that your build step has signing enabled and also that the Run Shell Script step is after your Build iOS Application build step.

####Locating your .ipa file

You'll need to find the .ipa file to deploy it to Crashlytics Beta. You have two options to do this:

We set the `$ARTIFACTS_DIRECTORY` environment variable. If you already know the expected .ipa name, you can find your .ipa by referencing `$ARTIFACTS_DIRECTORY/EXPECTED_IPA_NAME.ipa`.
You can use `find` to locate the .ipa as well. Example: `find . -iname *.ipa`

####Locating Crashlytics.framework

You'll also need to locate your Crashlytics framework. This typically is at the root of your iOS repository, but it may be located somewhere else. You can execute `find . -iname 'Crashlytics.framework'` to locate your Crashlytics.framework. 

####Finding your API key and build secret

You will also need your Crashlytics API key and build secret. You can find those by going to the Crashlytics [organizations page](https://www.crashlytics.com/settings/organizations), selecting your organization, and clicking the "API Key" and "Build Secret" links under the organization name.

####Deploying Release Notes

Ship.io currently does not have full support for deploying release notes with Crashlytics, but if you have release notes checked in to your repository, you can include those with the Crashlytics deploy command. 

####Deploying to Crashlytics Beta

Once you have located the .ipa file and your Crashlytics.framework, you'll need to execute the following command to deploy to Crashlytics Beta:

```
/path/to/Crashlytics.framework/submit **api-key** **build-secret** -ipaPath /path/to/my.ipa -emails developer1@ship.io,developer2@ship.io -notesPath ~/path/to/ReleaseNotes.txt
```

After that, save your changes to the Job, then go ahead and run the build.

####Example Run Shell Script Step

Here is an example shell script step that you can use as a basis for your ipa distribution step:

```bash
IPA_NAME=`find . -iname *.ipa`
CRASHLYTICS=`find . -iname 'Crashlytics.framework'`
if [ -f "$IPA_NAME" ] && [ -d "$CRASHLYTICS" ]; then
"$CRASHLYTICS/submit" api-key build-secret -ipaPath "$IPA_NAME" -emails **comma-separated-emails**
else
echo "Error deploying ipa to crashlytics: no ipa or crashlytics framework found!";
exit 1
fi
```

This script will find the IPA name and the location of the Crashlytics plugin. If those statements don't find the correct locations, you can set them manually. Be sure to leave quotes around the usage of `$IPA_NAME` and `$CRASHLYTICS` since the locations may have spaces in them. 

Plug in your API key, build secret, and comma separated list of emails. You should be set!
