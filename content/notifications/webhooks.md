/*
Sort: 4
*/
It is often useful to integrate your build process with other services, including your own backend. To support these types of integrations, Ship.io uses Webhooks to send HTTP POST requests that contain data about builds completed in our system. 

####Enabling Webhooks

To enable webhooks for your job, start by editing your Job and clicking "Manage Notifications".

![Manage Notifications](/images/notifications/manage-notifications.png)

From the Notifications dialog, select the webhooks tab and enter the URL of the endpoint you would like to receive the POST.
Webhook POST Format

![Webhooks Modal](/images/notifications/webhooks/modal.png)

Once a Webhook has been configured, Ship.io will send an HTTP POST to the specified URL whenever a build finishes. The body of the POST will contain JSON of the following format:

```json
{  
   "build":{  
      "id":"86db20de-32ff-467d-b139-1d0d1eb95ca7",
      "build_number":3,
      "commit_sha":"d4609e03c6059c90f9bd8b8dd6d7209c7aa769e9",
      "state":"succeeded",
      "successful":true,
      "artifacts":[  
         {  
            "id":"5f9aee35-7a02-483c-9f01-2400709fa32d",
            "name":"ShipIO.app.zip",
            "download_url":"https://ship.io/builds/86db20de-32ff-467d-b139-1d0d1eb95ca7/build_steps/s4ltNl77itaw6xIj/artifacts/ShipIO.app.zip?build_access_token: f6596e09b7a1be4c6"
         },
         {  
            "id":"8f165432-7751-4b81-86ee-efa2c2363c9d",
            "name":"ShipIO.app.dSYM.zip",
            "download_url":"https://ship.io/builds/86db20de-32ff-467d-b139-1d0d1eb95ca7/build_steps/s4ltNl77itaw6xIj/artifacts/ShipIO.app.dSYM.zip?build_access_token=f6596e09b7a1be4c6"
         },
         {  
            "id":"83cc567a-4cc6-47f4-a363-fde80c7c4dd3",
            "name":"ShipIO.build.zip",
            "download_url":"https://ship.io/builds/86db20de-32ff-467d-b139-1d0d1eb95ca7/build_steps/s4ltNl77itaw6xIj/artifacts/ShipIO.build.zip?build_access_token=f6596e09b7a1be4c6"
         }
      ]
   },
   "job":{  
      "id":"AQ_9V0GKpZ8Zkjj_",
      "name":"shipio-example-ios",
      "repository":{  
         "name":"shipio-example-ios",
         "selected_branch":"master",
         "html_url":"https://github.com/shipio/shipio-example-ios",
         "clone_url":"https://github.com/shipio/shipio-example-ios.git"
      }
   }
}
```
