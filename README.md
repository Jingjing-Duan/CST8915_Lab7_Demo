# Lab 7 - Kubernetes Basics
This lab demonstrates Kubernetes resource deployment and analyzes the RabbitMQ configuration issue in the Algonquin Pet Store application.

## Demo Video
YouTube Link: https://youtu.be/grWtF4-BUQc

## RabbitMQ configuration issues
- Is RabbitMQ stateless or stateful?
RabbitMQ is a stateful application because it stores queues, messages, and broker state.

- What happens without persistent storage?
Without persistent storage, RabbitMQ stores data inside the container.
If the pod is restarted or deleted, the data may be lost.
This includes queues and messages, which makes the system unreliable.

- What happens when pod is deleted?
When the RabbitMQ pod is deleted, Kubernetes automatically recreates it.
However, since there is no persistent storage, the new pod starts with empty data.
All previous messages and queues may be lost.

- Why is this a problem?
RabbitMQ is used for messaging between services.
If messages are lost, it can break communication between services and affect system reliability.

## Solutions
Possible solutions include:
- Using Persistent Volumes (PV) and Persistent Volume Claims (PVC)
- Using StatefulSet instead of Deployment
- Configuring durable queues and persistent messages

## Conclusion
RabbitMQ is a stateful application, but in this lab it is deployed without persistent storage.
This can lead to data loss when the pod is restarted.
Using persistent storage or managed services like Azure Service Bus can improve reliability.
