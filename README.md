# Corona Update Process for Camunda Cloud
This project contains a BPMN file. It is deployed to [Camunda Cloud](https://console.cloud.camunda.io).

You can find all the information [here](https://docs.camunda.io/docs/guides/) how to set up an own cluster and get the credentials for your workers. 

Deploy the model
You can take this model from the repo and build a client that deploys it. Here is a [tutorial](https://docs.camunda.io/docs/guides/setting-up-development-project#deploy-the-bpmn-model-to-camunda-cloud) how you can do that for different coding languages. 

Or you use the Cloud console to rebuild the model(as the model is small there is not a big problem). If you do so, you have to set few things in the properties panel: 
- Make sure to configure the service tasks with a type. This type is later important to connect the task workers
- Make sure you set expressions on the sequence flows after the XOR gateway
- Make sure to configure the timer.

The process runs in Camunda cloud based on the time start event and will start a new workflow instance every 24 hours. In order to run the process 4 Workers are needed. The workers are independ from each other and written in diffrent languages. You can find them here: 

- Corona Update worker
- Choose Activity worker
- Set celebration message worker
- Send Telegram message

