# Quantlytic - Stock Data Ingestor and ML Project

Quantlytic will be a full data pipeline for stock data data that includes ingesting live and historical data from API's, processing, training ML, and developing trades based on analytics. This is a hobby project and is unlikely to be used in a real trading environment. 

Project Goals:
* Learn about CI/CD with Kubernetes and github actions
* Create a microservice architecture
* Learn about Apache Kafka to create a pipeline capable of handling real time data
* Create a robust dataset for ML training

## Phases
### Phase 1 - Data Ingestion
The first phase of the project will be ingesting data. All freely available API's have rate limits and restrictions. To work towards creating a robust dataset, I'll want to get started on collecting data as soon as possible. The milestones in this phase are as follows:

- [x] Setup Apache Kafka on kubernetes
- [x] Setup MinIO Database on kubernetes for long term storage
- [ ] Create MinIO Write service to consume data from Apache Kafka topic
- [ ] Create live data api ingestor that writes to kafka topic
- [ ] Create historical data api ingestor to backfill dataset
- [ ] Create scheduler for historical data
