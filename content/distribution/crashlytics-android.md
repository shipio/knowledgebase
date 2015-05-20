/*
Title: Using Crashlytics Beta with Android
Sort: 1
*/

The Crashlytics team has made it very easy to configure your Gradle build to link in the Crashlytics library. First get an account with [Fabric](https://get.fabric.io/) and follow their instructions to get generally setup.

Once that's complete, you can define the list of testers to notify when a candidate app is uploaded to Crashlytics by adding the `ext.betaDistributionEmails` property to your app's `build.gradle` for your build type or flavor, like this:

```groovy
android {
  buildTypes {
    release {
      ext.betaDistributionEmails="tester1@c.com, tester2@c.com"
    }
    debug {
      ext.betaDistributionEmails="tester3@c.com, tester4@c.com"
    }
  }
}
```

You can instead reference a text file containing the addresses via the `ext.betaDistributionEmailsFilePath` property or a group via the `ext.betaDistributionGroupAliases` property.

Get more details for that [here](http://support.crashlytics.com/knowledgebase/articles/388925-beta-distributions-with-gradle).

To upload your built app and notify your testers, Crashlytics has provided the `crashlyticsUploadDistributionRelease` Gradle task for release builds and `crashlyticsUploadDistributionDebug` for debug builds. To use these tasks in Ship.io, define a new task in your `build.gradle` that depends on your build task and the appropriate Crashlytics task. For example:

`task buildAndOtaRelease(dependsOn: ['build', 'crashlyticsUploadDistributionRelease'])`

(That's really one line). NOTE: The example above assumes you use the `build` task to build your app. If you normally use a different task (say `mybuildtask`), create this new task to depend on that task (e.g. `dependsOn: ['mybuildtask', 'crashlyticsUploadDistributionRelease']`).

Commit and push the `build.gradle` update.

Now create your job in Ship.io. When you create your "Build an Android Gradle Project" step, choose your new task (`buildAndOtaRelease` in the above example). When you run the job, Ship.io will build your app and push it to Crashlytics and your testers.

If you have defined a job in Ship.io already, edit your job and click the 'update repository' link (see screenshot below) to re-scan your repository and make the new task available for your job. Then edit your build step, choose the new task, save, and you're all set.

####Multi-flavor variants
If you are using [build flavors](https://developer.android.com/tools/building/configuring-gradle.html#workBuildVariants), you will need to choose the flavor variant of the Gradle tasks described previously. For example, instead of `crashlyticsUploadDistributionDebug`, you should choose `crashlyticsUploadDistribution<build_flavor>Debug`.
