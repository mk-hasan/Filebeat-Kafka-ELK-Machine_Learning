# Anamoly Detection with ELK stack, KAFKA and Machine Learning. 


### What is ELK stands for?

The ELK stack is combination of multiple open source products. These are develpoed and well mainted by a company called Elastic.
Lets breakdown what ELK stands for:

* Elasticsearch - It lets you store, search and analyze data with scale
* Logstash - It filters parse each event, identify named fields to build structure, and transform them to converge on a common format for more powerful analysis
* Kibana - visualize data from diverse source with stunning dashboard, manage your deployment in a single UI.


we will start with the architecture breakdown then followed by a docker container configurations along with docker compose for each products. Finally, we will see how the architecture reads data and process through each components of the pipeline and visualize in Kibana dashboard and monitor. 

## The Architecture:

![Elk-kafka Architecture](/elk-archi.png "System Architecture")


To illustrate, the above figure represents the whole pipeline except the ML implementation. The first components Filebeat will read the log from any source then it will send the logs to the producer of the Kafka, the logstash will read the data from kafka broker then make some trsnformation or modifications followed by sending it to the Elsaticsearch. Finally Kibana will get the data from Elsaticsearch. 

## Start the Pipeline: 

Before starting the pipeline, we must configure the logstash configuration and we can also configure ans set certain filtering to get our necessary data. We have to give the input file path through logstash docker compose. Here i have given an example like access.log(simple log file). 

*  Up the Filebeat.yml file for running the filebeat service which will read the data from specific location or path and send it to kafka broker.
*  Up the kafka.yml file to start Kafka service which will also up the zookeeper and kafkabroker. Kafka will communicate with ELK stack and send the data from kafka topic. 
*  Up the docker-compose.yml (It will start running all the service). Logstash will get teh data from kafka topic according to the topic name and filter it according to your needs and then finally send it to elasticsearch. From the elasticsearch it can be process and visualize through kibana or use the data for ML model training/Testing. 

I am going to add the ML configuration in coming days. 

Please rate it with star if it helps you somehow. 

