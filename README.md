# Corona Update Process for Camunda Cloud
This project contains a BPMN file with a workflow. The workflow is deployed to [Camunda Cloud](https://console.cloud.camunda.io).
![Corona Update Process](/img/corona-update-process.png)

You can find all the information [here](https://docs.camunda.io/docs/guides/) how to set up an own cluster and get the credentials for your workers and clients to connect to Camunda cloud.


## Deploy the model: 

There are three options how you can deploy the model:

- :one: In order to make the model run in Camunda cloud some technical attributes have to be set. If you download the BPMN file and open it in the [Zeebe Modeler](https://github.com/zeebe-io/zeebe-modeler/releases) you can inspect those in the property panel.They are already set. You can also deploy your model from the Zeebe Modeler to your cluster. To do so you need to [connect it to your cluster](https://docs.camunda.io/docs/product-manuals/modeler/zeebe-modeler/connect-to-camunda-cloud)

- :two: You can take this model from the repo and build a client that deploys it. Here is a [tutorial](https://docs.camunda.io/docs/guides/setting-up-development-project#deploy-the-bpmn-model-to-camunda-cloud) how you can do that for different coding languages. 

- :three: If you just want to have a quick start you can also use the Camunda Cloud console to rebuilt this model quick (it is a nice and easy way to get started but if you probably won't use the modeling tool for production later)
If you do so, you have to set the technical attributes yourself
- Make sure to configure the service tasks with a type. This type is later important to connect the task workers
![Service task](/img/set-service-task-type.png = 100x)

- Make sure you set expressions on the sequence flows after the XOR gateway. The expression language used is [Feel](https://docs.camunda.io/docs/0.25/product-manuals/zeebe/reference/expressions/).
![Sequence flows after XOR](/img/set-expression-at-sequence-flow.png = 100x)

- Make sure to configure the timer.
![Timer start event](/img/set-timer-event.png = 100x)

The process runs in Camunda cloud based on the time start event and will start a new workflow instance every 24 hours. In order to run the process 4 Workers are needed. The workers subscribe to the topic that has been defined in the "type" field. The workers are independ from each other and written in diffrent languages. You can find them here: 

### Java Script Workers
- [Corona Update worker](https://github.com/Nlea/camunda-cloud-worker-corona-update)
- [Send Telegram message](https://github.com/Nlea/camunda-cloud-worker-send-Telegram-message)

### Java Workers
- [Choose Activity worker](https://github.com/Nlea/camunda-cloud-worker-choose-activity)
- [Set celebration message worker](https://github.com/Nlea/camunda-cloud-worker-send-Telegram-message)


