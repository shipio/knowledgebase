/*
Title: Using Gradle to Build an Android Project
Sort: 0
*/

[Gradle](http://www.gradle.org/) can automate the building, testing, publishing, deployment and more of software packages or other types of projects such as generated static websites, generated documentation or indeed anything else. Gradle combines the power and flexibility of [Ant](http://ant.apache.org/) with the dependency management and conventions of [Maven](http://maven.apache.org/) into a more effective way to build. Powered by a Groovy DSL and packed with innovation, Gradle provides a declarative way to describe all kinds of builds through sensible defaults. Gradle is quickly becoming the build system of choice for many open source projects, leading edge enterprises and legacy automation challenges.

Ship.io fully supports Android projects using Gradle. 

1. To get started using Gradle, create a new job and tie it to a repository containing an Android Gradle project (create a new job with GitHub).
2. Once the repository scan has completed, click "Add build step". 
3. Add a "Build Android Gradle" build step using the button dropdown on the far right.
4. In the build step settings, choose the Gradle task you'd like to use to compile your app (we intelligently suggest an option, but you are free to choose your own).
    - If your keystore is committed in your SCM system and your credentials for opening it are codified in your build.gradle, choose the <My keystore is in SCM> option.
    - Or you may choose have Ship.io generate a keystore for you and bind it to your build.
    - Or you may choose a keystore you've previously uploaded in the Code Signing page or a keystore that was created by Ship.io for some other build step in any of your jobs.
    - Except if your keystore is in SCM, Ship.io will make appropriate transient updates to your build.gradle file to sign your app with the chosen keystore.
5. Click "OK" and click "Create Job". Your new job will start automatically!
