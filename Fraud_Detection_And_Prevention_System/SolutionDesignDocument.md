# Fraud Detection And Prevention System
## Problem statement
Develop an advanced fraud detection and prevention system to
safeguard digital transactions and protect consumers and financial institutions
from fraudulent activities. Utilize machine learning algorithms and behavioral
analytics to analyze transaction data in real time, identify suspicious patterns,
and flag potentially fraudulent transactions for further investigation. Implement
multi-factor authentication mechanisms, anomaly detection techniques, and
transaction monitoring algorithms to enhance security and mitigate fraud
risks across various payment channels, including mobile payments, online
transactions, and peer-to-peer transfers. The solution should offer a seamless
user experience while maintaining robust security measures to combat
evolving fraud threats in the digital payments landscape.

## Proposed System Overview
The proposed system aims to:
1. Analyze transaction data in real-time and flag suspicious transactions.
2. Implement Multi-Factor Authentication(MFA).
3. Monitor transactions from multiple channels.
4. Seamless user experience.

## Proposed Solution:

An anti-fraud management system (AFMS) comprising fraud auditing, prevention, and detection tasks. Implementing real-time capabilities with streaming analytics technologies for these transactional and analytical workloads.

## 1. Real-Time Data Processing

> Real-time data processing is the execution of data in a short time, providing near instantaneous output. Examples of real-time data processing systems are bank ATMs, traffic control systems, and computer systems such as PCs, and mobile devices.
Real-time data processing is also called stream processing because of the continuous stream of input data required to yield output.

When you are trying to make any payment or withdraw money using a credit card the request is sent to your bank and the bank checks your pin and other details and determines whether to process the transaction or not. There is a time window between the request being sent and processing the request, during this very small time window we want to apply many operations: 

![Operations drawio](https://github.com/Sandesh3003/solution-design/assets/77960808/03eb0a4b-df10-4b28-85cf-25c80004e492)

#### a. Ingest: 
Collecting processing data from various sources in real or near-real time. Streaming data is a type of real-time data ingestion. In our case, the ingested data is the information regarding the transaction such as transaction number, credit card number, amount, device, geolocation, etc.

#### b. Enrich: 
Data Enrichment is the process of merging and adding either first-party or third-party data to a dataset you're already working with. In our case, we provide context, customer details, merchant details, and real-time features such as distance from home, etc to enrich the ingested data.

#### c. Transform:
In this operation, we do feature engineering to determine which features to use by performing normalizations, filtering, scaling, etc.

#### d. Predict:
This is where we have our trained machine learning model deployed in real-time and get fraud probability prediction.

#### e. Act:
After applying business rules and emerging fraud checks it gives output whether to accept or decline the transaction.

### Real-time stream processing in action:
To perform the above operations we will require an efficient event streaming pipeline. Stream processing is the foundation for implementing fraud detection and prevention while the data is in motion (and relevant) instead of just storing data at rest for analytics (too late).

For stream processing, we will be requiring stream processing engines like Apache Kafka. Apache Kafka is so good for real-time data streaming that it is even used by giant corporations like Twitter, Uber, Pinterest, Netflix, Tumblr, PayPal and many others. Its real-time data streaming abilities also make Apache Kafka an ideal choice for fraud detection. 

#### Using Apache Kafka for real-time data streaming:

![image](https://github.com/Sandesh3003/solution-design/assets/77960808/a63bd6af-986e-4dc5-a328-9788d3302e21)

Apache Kafka runs on a horizontally scalable cluster of commodity servers. It uses these servers to ingest real-time data from multiple systems and applications, known as producers.
Data is sent and received easily between Kafka servers. Changes in the state of the system are recorded as events.

Data can be transformed, read, and rewritten to topics. 
This data is then made available to a variety of consumer applications.
To explain in more detail, we can expand upon some of the key terms used above:

- **Producer:** a client application that pushes events into topics. Examples of producers include IoT devices, databases, or web apps.

- **Event:** A record of a change to the state of the system. Apache Kafka is an event streaming platform, meaning that it transmits data as events. It can publish and subscribe to a stream of events and store and process them as they occur.

- **Topic:** The method used to categorize and store events. They are logs that hold events in a logical order and enable data to be sent and received between Kafka servers easily. Older topic messages can be updated by newer topic messages, which allows data to be transformed.

- **Consumer:** Applications that read and process events from partitions. Java applications can pull data from topics and write results back to Apache Kafka, thanks to the Streams API.

Steps to implement real-time data streaming:
1. Create Kafka Producer: Develop a Kafka producer application to generate and publish streaming data.
2. Define Kafka Topics: Define Kafka topics to organize and manage the streaming data.
3. Implement Kafka Consumer: Develop a Kafka consumer application to consume and process the streaming data, here we will transform data by feature engineering.

Now, the next operation is prediction, evaluating the fraud probability.

## 2. Fraud prediction:

Machine Learning is used in fraud prediction due to its ability to analyze large quantities of data, identify patterns, and adapt to new information. 

The fraud detection is a classification and prediction problem. Supervised machine learning models have been proven as the best models in classifying and predicting financial transactions as either fraudulent or not using the decision tree, Logistic Regression, or Random Forest.

Fraud in digital transactions is an example of an imbalanced problem. Imbalanced learning addresses classification problems where the number of examples representing one class is much lower than the ones of the other classes. Learning from imbalanced datasets is a difficult task since most learning algorithms are not designed to cope with a large difference between the number of cases belonging to different classes.

![image](https://github.com/Sandesh3003/solution-design/assets/77960808/dea079be-58e7-4065-a95b-52c1f6697442)

Neural Network gives more accurate results than other models as it uses cognitive computing and it learns from the patterns of authorized behavior and thus distinguishes between ‘fraud’ and ‘genuine’ transactions. Comparatively to classical methods, there are an infinite set of hyperparameters and possibilities, which entails a time-consuming tuning process but allows a great expressivity.

### Fraud Detection using Neural Networks:

Neural Networks is a concept inspired by the working of a human brain. Neural networks in Deep Learning uses different layers for computation. It uses cognitive computing that helps in building machines capable of using self-learning algorithms that involve the use of data mining, pattern recognition, and natural language processing. It is trained on a dataset passing it through different layers several times.

![image](https://github.com/Sandesh3003/solution-design/assets/77960808/004db37c-a5b5-4a5a-b324-332437374edc)

Neural networks can detect fraud by learning from historical data and finding patterns or anomalies that indicate fraudulent behavior. For example, a neural network can analyze transactions and flag those that are unusually large, frequent, or out of the norm for a customer or a merchant. A neural network can also compare transactions with other sources of information, such as location, device, or biometric data, to verify the identity and authenticity of the parties involved.
 
Neural networks provide several advantages over traditional methods of fraud detection, such as they can generalize to unseen cases by inferring from the data they have learned and making predictions for new or rare situations. Lastly, neural networks can provide probabilistic outputs, such as confidence scores or likelihood ratios, that can help you assess the risk and severity of fraud.

The study on the performances for the feed-forward neural network, the convolutional neural network, the long short term memory, and the LSTM with Attention is discussed here:
https://fraud-detection-handbook.github.io/fraud-detection-handbook/Chapter_7_DeepLearning/RealWorldData.html

The sequential models(CNN models) are better than the regular feed-forward network, suggesting that the information brought by the history of transactions is relevant for fraud detection. The LSTM performs better than the CNN for the set of chosen hyperparameters, and the Attention brings a little value.
