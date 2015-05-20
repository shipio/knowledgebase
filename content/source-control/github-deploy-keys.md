/*
Title: GitHub Deploy Keys
Sort: 2
*/

Sometimes it can be advantageous to connect to GitHub using a Deploy Key rather than by connecting your GitHub Account. Fortunately, this is very straightforward to do using Ship.io's support for SSH keys.

1. First, let's start by generating a new SSH Key. Start by selecting "SSH Keys" from the drop down menu, and clicking "Generate Key Pair". This will generate a new public/private key pair that you can use as your SSH Key. However, if you prefer to add an existing key-pair you can select "Add My Own Key".

    ![SSH Key Index](/images/ssh/index.png)

2. Give your SSH Key a name and select "Save". This will generate a new key-pair and add it to your list of available SSH Keys.

    ![SSH Key Added](/images/ssh/key.png)

3. The next step is to grant this SSH Key access to pull your GitHub repository. On GitHub, navigate to your repository and select Settings. From there, click on the option for Deploy Keys. On this page you'll see a list of any Deploy Keys that you have configured with access to this repository (if any).

    ![Github Deploy Keys (empty)](/images/github/deploy-keys-empty.png)

4. Now, click the "Add deploy key" button, and copy the **public key** from Ship.io.

    ![SSH Key Expanded](/images/ssh/key-expanded.png)

5. Paste the **public key** into the text field on GitHub.

    ![Github Add Key](/images/github/add-deploy-key.png)

6. Click "Add key" and you should see your SSH Key listed under Deploy keys. Now, Ship.io is all setup to pull your code!

    ![Github Deploy Keys (one)](/images/github/deploy-keys.png)

7. Finally, back on Ship.io, setting up a Job using this repository is easy. When creating your Job, simply enter the SSH URL of your repository, the branch and select your SSH Key from the drop down list.
