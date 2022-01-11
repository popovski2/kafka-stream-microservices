# Kafka streaming microservices application


(***)

## Microservices 
'domain-crawler' - uses Spring Kafka
'domain-processor' - uses Spring Cloud Stream with Kafka Streams binder
'domain-service' - uses Spring Cloud Stream with Kafka Streams binder

## Endpoint
http://localhost:8080/domain/lookup/ + "name"  - to pull all web domain names related to some topic
Example: http://localhost:8080/domain/lookup/twitter - to pull all twitter related web domain names

## Architecture
