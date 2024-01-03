--
title: Machine Learning on AWS (Technical)
date: 2023-10-30
attendance: remote
tags:
  - AWS Partner Training
---

## Outline

- Module 1: Introduction to Machine Learning
- Module 2: Artificial Intelligence Services on AWS
- Module 3: Machine Learning Process
- Module 4: Data Collection, Integration, Preparation, Visualization, and Analysis
- Module 5: Deep Learning Amazon Machine Images
- Module 6: Amazon SageMaker Concepts
- Module 7: Amazon SageMaker Notebooks
- Module 8: Amazon SageMaker Built-In Algorithms
- Module 9: Amazon SageMaker Training, Debugging and Monitoring
- Module 10: Introduction to MLOps
- Module 11: Next Steps and Additional Learning
- Module 12: End of Course Assessment

## Workshop

- https://catalog.workshops.aws/sagemaker-fraud-detection/en-US
- Deploying a complete machine learning fraud detection solution using Amazon SageMaker
- Includes data preparation, feature engineering, and model training

## Resources

- [Amazon SageMaker Studio Lab](https://studiolab.sagemaker.aws/)
  - Based on JupyterLab, stripped-down version of SageMaker Studio
  - Place to run machine learning notebooks for free, provides GPU compute capabilities
  - Not integrated with AWS in general (from the user's perspective), i.e. don't need an AWS account for using it
- [Machine Learning University](https://aws.amazon.com/machine-learning/mlu/)
  - Initially built for AWS employees
  - Released to the public because it was so successful
- Futher resources
  - [Dive into Deep Learning](https://d2l.ai/index.html)
    - Book with hands-on labs
  - [Kaggle](https://www.kaggle.com/)
    - Community with machine learning competitions
  - [AWS Deep Racer](https://aws.amazon.com/deepracer/)
    - Simulator for autonomous driving with Deep Learning
  - [BloombergGPT](https://arxiv.org/abs/2303.17564)
    - Foundation model for finance
    - Private model, not available to the public
    - Over 10,000 hours of GPU processing to create the model
    - Cost goes into millions of dollars to create model
  - Introduction to precision, recall, and F1
    - https://www.youtube.com/watch?v=jJ7ff7Gcq34
  - Introduction to the confusion matrix
    - https://www.youtube.com/watch?v=wpp3VfzgNcI

## AWS machine learning stack

1. AI services
  - AI API layer
  - Usage: set up AWS Python SDK, create a client for the API, and make requests to the API
  - Vision, Speech, Text, Search, Chatbots, Personalize, Forecast, Fraud, Development, Contact Centers
  - Example services
    - [Amazon Rekognition](https://aws.amazon.com/rekognition/)
      - Recognise and classify objects in images
      - Bounding boxes of recognised objects
      - Facial sentiment recognition
    - [Amazon Textract](https://aws.amazon.com/textract/)
      - OCR and analysis of documents
      - Automatically create data store of extracted data
    - [Amazon Comprehend](https://aws.amazon.com/comprehend/)
      - Comprehend text
    - [Amazon Personalize](https://aws.amazon.com/personalize/), [Amazon Forecast](https://aws.amazon.com/forecast/), [Amazon Fraud Detector](https://aws.amazon.com/fraud-detector/)
      - Based on Amazon's retail experience and data sets
      - Amazon Personalize: personalised recommendations (e.g. for products)
      - Amazon Forecast: time-series forecasting (e.g. for demand)
      - Amazon Fraud Detector: detect frauds related to new accounts, online payment, guest checkout
    - [Amazon Kendra](https://aws.amazon.com/kendra/)
      - Enterprise search service across multiple data stores
      - Can be intergrated with chatbots
1. ML services
  - SageMaker
  - [SageMaker Ground Truth](https://aws.amazon.com/sagemaker/data-labeling/)
    - Automatic labelling of training data, label management
    - Integrates with human labelling services, such as [Amazon Mechanical Turk](https://www.mturk.com/), as well as third-party services
1. ML framework and infrastructure
  - Inferentia and Trainium chips
  - Support for ML frameworks including TensorFlow, PyTorch, and MXNet

## Data collection, integration, and preparation

- [Amazon Athena](https://aws.amazon.com/athena/)
  - Serverless way to run SQL commands on data sets
- [Amazon Quicksight](https://aws.amazon.com/quicksight/)
- [Amazon Lake Formation](https://aws.amazon.com/lake-formation/)
- [Amazon SageMaker Data Wrangler](https://aws.amazon.com/sagemaker/data-wrangler/)
  - Allows creating visual data flows
  - Data sources may be S3, Athena, Redshift, EMR, Snowflake
  - Allows including steps, like transformations, analyses and visualisations, in the flow
    - Example: dropping, transforming columns, etc.
- [AWS Glue](https://aws.amazon.com/glue/)
  - Similar to SageMaker Data Wrangler
  - Creates Spark jobs (in Python) in the background
  - Visualisation of data flows with Visual ETL
- [AWS Glue DataBrew](https://aws.amazon.com/glue/features/databrew/)
  - Similar to AWS Glue but includes visualisation for every step
- [Amazon EMR](https://aws.amazon.com/emr/)
  - Elastic MapReduce (EMR)
  - Run and scale big data workloads (Spark, Hive, Presto)
- Four ways to do data collection, integration, and preparation:
  1. SageMaker Data Wrangler: most popular
  1. AWS Glue
  1. AWS Glue DataBrew
  1. Amazon EMR: high performance but complex

## Old machine learning approaches

- Deep learning AMIs on EC2
  - Search for "Deep Learning" in the [AMI Catalog](https://us-west-2.console.aws.amazon.com/ec2/home?region=us-west-2#AMICatalog:) in the EC2 Console
  - **Do not** use ad-hoc EC2 instances with these AMIs as this approach is deprecated
    - Use services like SageMaker instead
- SageMaker Notebook
  - Allows creating notebook instances running vanilla JupyterLab
  - Successor of machine learning AMIs on EC2 and predecessor of SageMaker Studio
  - Use SageMaker Studio instead

## MLOps

- Differs from DevOps in that it has a more complex and circular nature
  - Data from inference monitoring cycles back into model training
  - More complex orchestration than DevOps
- Main processes
  1. Data preparation
  1. Model building and training
  1. Model deployment and monitoring
- [Amazon SageMaker Pipelines](https://aws.amazon.com/sagemaker/pipelines/)
  - Sets up Step Functions and CodeCommit repository
- [Kubeflow](https://www.kubeflow.org/)
  - Can be run on top of SageMaker
  - SageMaker operator for Kubernetes
