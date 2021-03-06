# Kafka streaming microservices application


## Description
The app I built is using Kafka into Spring Boot application.  

domain-crawler is the **Kafka Producer** that scrapes the data from https://api.domainsdb.info/v1/domains/, where it can find active or inactive domains on the internet. The specific topic on which it scrapes is the name which we provide through the *endpoint* (see below). Once the domain-crawler got the information, it publishes on kafka topic named **web-domains**.  

*Note: By here, I am using Spring Kafka, not Kafka Streams  

From the **web.domains** topic, I am consuming the data using **domain-processor** (Kafka Streams microservice) using Spring boot (Spring Cloud Streams). Here the Kafka Streams processor is filtering out only the active domains and publishing them on the new **active.web-domains** topic.  

From the **active.web-domains** topic, I am consuming the message via the **domain-service** and I am logging them.  

## Microservices 
'domain-crawler' - uses Spring Kafka  
'domain-processor' - uses Spring Cloud Stream with Kafka Streams    
'domain-service' - uses Spring Cloud Stream with Kafka Streams    


## Endpoint
http://localhost:8080/domain/lookup/ + "name"  - to pull all web domain names related to some topic  
Example: http://localhost:8080/domain/lookup/twitter - to pull all twitter related web domain names


## Architecture  
![kafka_arhitektura](kafka_architecture.png)

## Video 
https://drive.google.com/file/d/1DlJY7r27PU6oymzyI0ZAUILTzVwTlfqd/view?usp=sharing

### References
[1] https://javatechonline.com/how-to-work-with-apache-kafka-in-spring-boot/  
[2] https://www.youtube.com/watch?v=rqjdSbIOrJ4&ab_channel=TechPrimers
