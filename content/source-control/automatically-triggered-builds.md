/*
Sort: 3
*/

Ship.io supports the automatic triggering of builds by both commit hooks and polling.

##Commit Hooks

Ship.io currently supports builds triggered by commit hooks from Github and BitBucket.

*NOTE: If the head (last) commit message of a triggered hook contains the tokens **[ci skip]** or **[skip ci]**, Ship.io will ignore that hook and will not trigger a build.*

###GitHub

If you have your GitHub account connected to your Ship.io account, Ship.io will automatically attempt to create a commit hook when you create a job. If this fails, you're always able to manually create the commit hook.

1. Go to your GitHub repository, and click the "Settings" tab on the right.
2. Click the "Webhooks" tab. 
3. Click the "Add Webhook" button and fill in the following data. 

###BitBucket

1. Go to your BitBucket repository settings, and click the "Hooks" tab. 
2. Click the "Select a hook" dropdown, and choose the "POST" hook. Click "Add hook". 
3. In the "URL" text field, paste the following URL: https://api.ship.io/commit_hook?service=bitbucket 

##Polling

If you select "Polling" when creating your job, Ship.io will clone your repository every 10 minutes and check for any changes since the last build. If changes are detected, Ship.io will queue a new build.
