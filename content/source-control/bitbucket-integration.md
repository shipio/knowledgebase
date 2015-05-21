/*
Sort: 1
*/

[Bitbucket](https://bitbucket.org) is another popular hosting provider for Git source code repositories, which Ship.io fully supports through the use of SSH Keys. Follow these steps to connect your Bitbucket repository to Ship.io.

1. Let's start by generating a new SSH Key. Start by selecting "SSH Keys" from the drop down menu, and clicking "Generate Key Pair". This will generate a new public/private key pair that you can use as your SSH Key. However, if you prefer to add an existing key-pair you can select "Add My Own Key".
2. Give your SSH Key a name and select "Save". This will generate a new key-pair and add it to your list of available SSH Keys.
3. The next step is to grant this SSH Key access to pull your Bitbucket repository. On Bitbucket, navigate to your repository and click the Settings icon. From there, select "Deployment Keys" in the main pane. On this page you'll see a list of any Deployment keys you have already configured with access to this repository (if any).
4. Now, click the "Add key" button and copy the Public Key from Ship.io and paste it into the Key field on Bitbucket.
5. Click "Add key" and you should see your SSH Key listed under Deploy keys. Now, Ship.io is all setup to pull your code!
6. Finally, back on Ship.io, setting up a Job using this repository is easy. When creating your Job, simply enter the SSH URL of your repository, the branch and select your SSH Key from the drop down list.
 
####Bitbucket Commit Hooks

Ship.io has full support for builds automatically triggered by Bitbucket POST hooks. Read more about this feature [here](%base_url%/source-control/bitbucket-integration).
