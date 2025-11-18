# Assignment 2: Cloud Service Providers Comparison Report

## Assignment Overview

Conduct a comparison of **AWS**, **Azure**, and **GCP** focusing on their cloud services for remote data and real-time applications. Submit your report as a README.md file in a public GitHub repository.

---

## Report Structure & Requirements

### 1. Executive Summary (10%)

This assignment compares and analyzes AWS, Azure, and GCP and their different services for remote data streaming, real-time applications, and various APIs. The report then evaluates how each CSP can support workloads that require low latency, scalable data ingestion, and real-time streaming analytics in two hypothetical use cases.

The comparison will address their services for RESTful APIs, GraphQL, WebSocket, data streaming, and stream analytics. Pricing, scalability, performance and integration is compared across various services. Some CSPs fully support a capability in a packaged service, while other CSPs provide the service across various services running and integrated together. Some CSPs also fully apply a capability within a service, while others only permit an import into a more general management service.

As previously mentioned, two hypothetical use cases will be explored to contextualize the strengths of each CSP and their remote data or real-time services. While each CSP provides services for each category in the comparison, the report will thoroughly explore how they differentiate, and how an organization should determine the best platform to pursue their remote data or real time project with.

### 2. Introduction (10%)

#### Purpose & Scope

This assignment will help us understand the differences and similarities between the three major CSPs (AWS, Azure, GCP) and the services they offer for building and deploying remote data and real-time application solutions. The scope of this assignment covers the various remote data and real-time application contexts we explored in class over the past semester:

- Remote data: IoT, other distributed systems
- Real-time communication: WebSockets, data streaming pipelines, event-driven architecture, edge computing

#### Overview: AWS, Azure, GCP

1. AWS:
Compared to the other two CSPs, AWS stands out as the most mature CSP that holds the largest market share. If an organizations wants a comprehensive and flexible list of solutions, they should consider AWS first.
2. Azure:
Azure is integrated closely within Microsoft's ecosystem, so their services are particular ideal for organizations that already use Microsoft tools like their Office suite.
3. GCP:
GCP highlights Google's prowess in data analytics, AI, and open source development practices. Organizations that prioritize the most bleeding edge analytics tools should look to GCP for their remote data needs.

### 3. Service Comparison (60%)

Compare the three CSPs across these categories:

- Amazon Kinesis Data Streams [1]: This service allows users "to collect and process large streams of data records in real time" and create Kinesis applications from it. From there, you can use processed records to display on dashboards, generate alerts, dynamically trigger changes in other services, or forward data to other services.
- AWS Lambda [2]: This service allows users to run "code without the need to manage servers." Its real-time use case includes the ability to "process real-time data streams for analytics and monitoring" and "handle...IoT...requests."
- AWS IoT [3]: This service "provides the cloud services that connect your IoT devices to other devices and AWS cloud services." In particular, AWT IoT Core helps "manage and support...IoT devices in the field" over MQTT/WSS and LoRaWAN (low-power long-range Wide Area Network)devices

**a) RESTful API Services (15%)**

- AWS: **Amazon API Gateway** [1] supports RESTful APIs (REST and. HTTP) that are "optimized for serverless workloads" like Lambda. They provide ample documentation for both REST and HTTP endpoints that API Gateway can create for the API. The REST API can include features like "API keys, per-client throttling, request validation, AWS WAF integration, or private API endpoints." 
  - Free up to 1M calls, then staggered tier pricing per call; $3.50 per million for the first 333M, then $2.80 per for the next 667M, and so on.
- Azure: **Azure API Management** [2] supports REST API publishing, versioning, throttling, and monitoring. API Management supports APIs hosted on Azure, on-premises, or other clouds. It is directly integrated with Log Analytics in the portal, and thus promotes not just being a proxy/gateway, but a full API Management suite (as the name suggests); policies for transforming payloads calling the API, analytics, alerts, etc.
  - Tier-based (Basic, Standard, Premium v2) with fixed monthly prices up to a certain number of requests (10M, 50M, unlimited), then pay-per-call (except for Premium)
- GCP: **Google Cloud API Gateway** [3] provides "secure access to your backend services through a well-defined REST API that is consistent across all of your services, regardless of the service implementation." It streamlines developer access to services and allows you to update backend service implementation without having to touch the public API.
  - Free up to 2M calls, then staggered tier pricing per call; $3.00 per million for the first 1B, then $1.50 afterwards.

**b) GraphQL Services (15%)**

- AWS: **AWS AppSync** [4] allows developers "connect their applications and services to data and events with secure, serverless and high-performing GraphQL APIs." The applications through AppSync can access 1+ data sources via a single GraphQL endpoint or combine multiple GraphQL endpoints into a single merged on.
  - You can integrate this with any third party GraphQL engine like Hasura, Apollo, or both.
- Azure: **Azure API Management** [5] also supports GraphQL API by passing through to an existing GraphQL endpoint you have or importing a GraphQL schema (via Azure CLI) and creating a synthetic GraphQL API based on that.
  - Like AWS, you can integrate any third party GraphQL engine like Hasura or Apollo by configuring its endpoint in API Management.
- GCP: **Apigee** [6] is GCP's native API management platform that allows you to upload a GraphQL schema to it. From there, the GraphQL policy allows developers to enforce APIs to conform to a provided schema, impose restrictions on the payload, and authenticate it with various Apigee policies. 
  - Like the other two CSPs, you can use any GraphQL engine (Hasura, Apollo) by configuring the endpoint to the management platform.

**c) WebSocket Services (10%)**

- AWS: **Amazon API Gateway** [7] also supports "collection[s] of WebSocket routes that are integrated with backend HTTP endpoints, Lambda functions, or other AWS services." The predefined routes in API Gateway include "`$connect` and `$disconnect`" which act as the handshake and closing frame respectively.
  - API Gateway supports scalability by offloading the persistent connections to API Gateway instead of applications, like in EKS. [8] By separating connection management from application logic, Kubernetes workloads can scale more efficiently.
- Azure: **Azure API Management and Azure Web PubSub** [9] [10] both allow developers to integrate WebSocket into their ecosystem, either by importing an existing endpoint into a central management plane (API Management) or by using WebSocket protocol as an option to enable realtime messaging via a pub/sub structure (Web PubSub)
  - Web PubSub can autoscale to handle thousands of simultaneous connections at once.
- GCP: **Cloud Run** [11] allows developers to run WebSocket applications on Cloud Run as a streaming service. You can do so as simply as building the service with the Google Cloud CLI within the service Git repo.
  - Cloud Run is able to autoscale out instances to handle streaming and connection demand.


**d) Data Streaming Services (10%)**

- AWS: **Amazon Kinesis Data Streams** [12]: allows developers "to collect and process large streams of data records in real time" and create Kinesis applications from it. From there, you can use processed records to display on dashboards, generate alerts, dynamically trigger changes in other services, or forward data to other services.
- Azure: **Azure Event Hubs** [13] is a data streaming service that can handle millions of events per second with low latency, from any number of sources to any destination. Event Hubs handles both ingestion and storing data streams to gain insights and drive real-time analytics. In essence, it acts as a buffer that ingests data for the destination.
  - **Azure IoT Hubs** [17] is a data streaming service for physical IoT devices, and acts as a central message hub for them. It enables secure and reliable communicate at any scale between IoT devices and applications.
- GCP: **Google Cloud Pub/Sub**  [14] ingests and distributes event data streams to destination sources like the AI-enabled Dataflow. It operates on a pub/sub system with messages/topics. It is designed to fetch and deliver messages instantly across millions of messages all around the world.

**e) Stream Analytics (10%)**

- AWS: **Amazon Kinesis Data Stream** [12] can also run real-time analytics on the event data via integrations with AWS Lambda.
- Azure: **Azure Stream Analytics** [15] is a stream processing engine designed to analyze, and process huge volumes of data streams with extremely low latency. Within the data streaming pipeline, it acts as a "data detective" that identifies patterns and relationship in the data based on its sources. These identified patterns can be used to trigger actions or initiate more workflows like alerts, dashboards, or storage.
- GCP: **Google Cloud Pub/Sub, Dataflow, and BigQuery** [16] comprise Google Clouds stream analytics infrastructure. The three of them combined help to ingest, process, and analyze any volume of real time data for equally real time insights and action triggers. In particular, **Dataflow** plays the biggest role in stream analytics by enabling real-time ETL pipelines for rapid, AI-powered analysis and decision making.

### 4. Use Case Analysis (15%)

1. **Real-time trading platform**: A fintech company has to be able to process millions of stock trades per second and deliver equally live price updates to users. Low latency is critical here for expected decision-making accuracy.
   1. Requirements
      1. Extremely low latency
      2. Scalable, persistent, bidirectional WebSocket connections for trader clients
      3. Real time stream analytics to detect fraud
   2. CSP recommendation: **AWS**
      1. Cost: Pay-per-call pricing for API Gateway is ideal for bursts of demand. Autoscaling is helpful to keep costs efficient as well.
      2. Performance: API Gateway WebSocket APIs scale elastically and takes care of connection management for any EKS clusters, while Kinesis simultaneously handles data ingestion and stream analytics.
      3. Ease of Integration: The system can easily integrate API Gateway and Kinesis with Lambda, DynamoDB, and EKS for a full pipeline.
      4. Ecosystem: AWS has the largest and most mature services out of all the CSPs, and thus has the most reliable compliance certifications for an industry as stringent as the finance industry. 
2. **Smart city traffic management**: Ottawa deploys IoT cameras with sensors (again...) that monitor traffic flow, detect congestion, and adjusts traffic signals dynamically. The system needs to ingest remote sensor data, process it in real time, and display results on easy-to-read dashboards for city planners.
   1. Requirements
      1. High throughput ingestion from thousands of cameras
      2. Real-time stream analytics to optimize traffic signals
      3. Easy integration with powerful visualization tools
   2. CSP recommendation: **Azure**
      1. Cost: Both IoT Hubs and Stream Analytics offer tiered pricing, which provides predictability for static public budgets.
      2. Performance: Azure IoT Hubs and Stream Analytics provide high-throughput ingestion (thousands of telemetry streams from cameras) to ensure that traffic data is captured without any bottleneck in the streams. In addition, they have extremely low latency, so traffic signals can be adapted in real time; if a jam is detected, the signals can instantly react to it. They also autoscale, so even peak traffic like 4-6pm will not affect performance.
      3. Ease of Integration: Processed data from Stream Analytics can easily flow into Power BI dashboards with real-time refreshes, so city planners can track traffic conditions' live updates.
      4. Ecosystem: Azure tightly integrates with other Microsoft services, and Ottawa already uses the Microsoft 365 and Office suite, so the city can easily integrate the system within their existent traffic monitoring applications as well.

### 5. Conclusion (5%)

- Summary of findings and overall recommendations

AWS, Azure, and GCP have similarities and differences across REST/GraphQL/WebSocket API services, data streaming services, and stream analytics services. AWS' strength lies in its large and mature ecosystem, where you can integrate any API into their API Gateway and handle data streaming and streaming analytics via Kinesis. Azure shines within enterprise contexts that are already tightly integrated with Microsoft's suite of services, and they are notable for having a specific fully managed Stream Analytics services that integrates easily with ingestion services like Event Hubs or IoT Hubs. GCP demonstrates their prowess in their cutting edge, AI-powered analytics suite across Pub/Sub (ingestion), Dataflow (stream processing), and BigQuery. (insights) In summary, AWS would be best for general purpose real time streaming, particularly if you in in a highly regulated industry. Azure would be ideal if the organization is already integrated with Microsoft services or if the organization is seeking an out of the box "data detective" stream analytics service. Finally, GCP should be chosen if they are pursuing AI-powered analytics pipelines.

### 6. References

[1]
“What Is Amazon API Gateway? - Amazon API Gateway,” AWS, 2019. https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html

[2]
“Azure API Management - Overview and key concepts,” Microsoft. Sep. 29, 2022. Available: https://learn.microsoft.com/en-us/azure/api-management/api-management-key-concepts

[3]
“API Gateway documentation  |  Google Cloud Documentation,” Google Cloud Documentation, 2025. https://docs.cloud.google.com/api-gateway/docs (accessed Nov. 18, 2025).

[4]
“What is AWS AppSync? - AWS AppSync,” docs.aws.amazon.com. https://docs.aws.amazon.com/appsync/latest/devguide/what-is-appsync.html

[5]
“Add a GraphQL API to Azure API Management,” Microsoft.com, Oct. 07, 2025. https://learn.microsoft.com/en-us/azure/api-management/graphql-api?tabs=portal (accessed Nov. 18, 2025).

[6]
“Using GraphQL,” Google Cloud Documentation, 2025. https://docs.cloud.google.com/apigee/docs/api-platform/develop/graphql (accessed Nov. 18, 2025).

[7]
“Working with WebSocket APIs - Amazon API Gateway,” AWS. https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-websocket-api.html

[8]
J. Dedhia and K. Sung , “Optimize webSocket applications scaling with API Gateway on Amazon EKS | Amazon Web Services,” AWS, Oct. 06, 2023. https://aws.amazon.com/blogs/containers/optimize-websocket-applications-scaling-with-api-gateway-on-amazon-eks/ (accessed Nov. 18, 2025).

[9]
“Import a WebSocket API to Azure API Management,” Microsoft.com, Feb. 20, 2025. https://learn.microsoft.com/en-us/azure/api-management/websocket-api?tabs=portal (accessed Nov. 18, 2025).

[10]
“What is Azure Web PubSub service?,” Microsoft, May 28, 2025. https://learn.microsoft.com/en-us/azure/azure-web-pubsub/overview

[11]
“Using WebSockets,” Google Cloud Documentation, 2025. https://docs.cloud.google.com/run/docs/triggering/websockets (accessed Nov. 18, 2025).

[12]
“What Is Amazon Kinesis Data Streams? - Amazon Kinesis Data Streams,” AWS. https://docs.aws.amazon.com/streams/latest/dev/introduction.html

[13]
“What is Azure Event Hubs? - a Big Data ingestion service - Azure Event Hubs,” learn.microsoft.com, Dec. 17, 2024. https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-about

[14]
“Pub/Sub for Application & Data Integration,” Google Cloud. https://cloud.google.com/pubsub?hl=en

[15]
“Introduction to azure stream analytics,” learn.microsoft.com, Dec. 17, 2024. https://learn.microsoft.com/en-us/azure/stream-analytics/stream-analytics-introduction

[16]
“What is streaming analytics?,” Google Cloud, 2024. https://cloud.google.com/learn/what-is-streaming-analytics?hl=en (accessed Nov. 18, 2025).

[17]
“IoT concepts and Azure IoT Hub,” Microsoft, Feb. 24, 2024. https://learn.microsoft.com/en-us/azure/iot-hub/iot-concepts-and-iot-hub