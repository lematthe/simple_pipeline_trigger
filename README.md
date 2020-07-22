# Simple Pipeline/Webhook

## Deploying
You can create the pipeline in any order but the logical creation order is task, pipeline, triggers. The TaskRun does not need to be used.

Once the triggers have been created, an EventListener service/pod will be created and this needs to be exposed so that GitHub can call it when a push is created.

Do not for get to add the URL to the WebHook page of your Git repo in order to trigger the pipeline build. Make sure the webhookm sends application/json which is
expected by the event listener.

To determine what is provided in the JSON payload for an event (in this case push):  [WebHooks Payload - Push](https://developer.github.com/webhooks/event-payloads/#push).

In this case we are only pulling the commit comment (body.head_commit.message) in the trigger binding.

