# Corona Update Process for Camunda Cloud
This project contains a BPMN file.

The file is deployed to Camunda Cloud. You find information here, how you can deploy the process model to your Camunda Cloud Cluster. 

The process runs in Camunda cloud based on the time start event. In order to run the process 4 Workers are needed. The workers are independ from each other and written in diffrent languages. You can find them here: 

- Corona Update worker
- Choose Activity worker
- Set celebration message worker
- Send Telegram message
