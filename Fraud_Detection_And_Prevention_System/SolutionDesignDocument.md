# Fraud Detection And Prevention System
## Problem statement
Develop an advanced fraud detection and prevention system to
safeguard digital transactions and protect consumers and financial institutions
from fraudulent activities. Utilize machine learning algorithms and behavioral
analytics to analyze transaction data in real-time, identify suspicious patterns,
and flag potentially fraudulent transactions for further investigation. Implement
multi-factor authentication mechanisms, anomaly detection techniques, and
transaction monitoring algorithms to enhance security and mitigate fraud
risks across various payment channels, including mobile payments, online
transactions, and peer-to-peer transfers. The solution should offer a seamless
user experience while maintaining robust security measures to combat
evolving fraud threats in the digital payments landscape.

## Proposed System Overview
The proposed system aims to:
1. Analyze transaction data in real time and flag the suspicious transactions.
2. Implement Multi-Factor Authentication(MFA).
3. Monitor transactions from multiple channels.
4. Seamless user experience.

## Proposed Solution:

### 1. Real Time Data Processing

> Real-time data processing is the execution of data in a short time period, providing near instaneous output. Examples of real-time data processing systems are bank ATM's, traffic control systems and computer systems such as PCs, mobile devices.
Real-time data processing is also calleed stream processing because of continuous stream of input data required to yield output.

When you are trying to make any payment or withdraw money using credit card the request is sent to your bank and the bank checks your pin and other details and determines whether to process the transaction or not. There is a time window between the request is sent and processing the request, during this very small time window we want to apply many operations: 

![Operations drawio](https://github.com/Sandesh3003/solution-design/assets/77960808/03eb0a4b-df10-4b28-85cf-25c80004e492)

#### 1. Ingest: 
Collecting processing data from various sources in real or near-real time. Streaming data is a type of real-time data ingestion. In our case, the ingested data is the information regarding the transaction such as transaction number, credit card number, amount, device, geolocation, etc.

#### 2. Enrich: 
Data Enrichment is the process of merging and adding either first-party and third-party data to a dataset you're already working with. In our case, we provide context, customer details, merchant details and real time features such as: distance from home etc to enrich the ingested data.

#### 3. Transform:
In this operation we do feature engineering to determine which features to use by performing normalizations, filtering, scaling, etc.

#### 4. Predict:
This is where we have our trained machine learning model is deployed in real time and get fraud probability prediction.

#### 5. Act:
After applying business rules and emerging fraud check it gives output whether to accept or decline the transaction.

