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

### Phase 2 - Data Processing and Cleaning
The second phase will mostly iterate on the first phase. The biggest new feature will be the data preprocessing service, which will consume raw API data and perform various transformations and calculations that will be essential for training ML models. Furthermore, data will be stored in a Time Series Database after processing. Other goals for this phase are identifying gaps in the dataset and sending tasks to the scheduler to fill those gaps.

### Phase 3 - ML Architecture
The third phase involves establishing the architecture needed to begin training and evaluating ML models based on the dataset. 

### Phase 4 - IBKR Integration
Using Interactive Brokers' API, execute trades in a paper trading (simulated) environment to evaluate the performance of the models. 

## Architecture

### Data Pipeline
* Data is ingested from API and placed in kafka topic
* Raw data is stored in Minio as source of truth
* Raw data is preprocessed
* Preprocessed data is stored in TSDB
* ML models automatically train and infer on processed data
* ML output data is stored in TSDB
* Trades are created, evaluated, and possibly executed based on processed data and ML outputs

The diagram below is a high level overview of the pipeline described in bullet points above. Each unit may be composed of multiple microservices that work together.
<img width="791" height="512" alt="DataFlowPipeline" src="https://github.com/user-attachments/assets/8781339f-0e0d-41f2-be95-8a7c623eadee" />

