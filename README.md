#Anamoly Detection with ELK stack, KAFKA and Machine Learning. 


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

