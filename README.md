## AWS-SAA-C01-Study-Guide

Note these are my own personal notes and are a work in progress as I study towards passing this exam.  If this helps someone great, but I make no guarantees/promises.  

## Table of Contents
1. <a href="#introduction">Introduction</a>

## Introduction
<a href="https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS_Certified_Solutions_Architect_Associate-Exam_Guide_EN_1.8.pdf">AWS Certified Solutions Architect Associate (SAA-C01) Exam Guide</a>

<a href="https://certmetrics.com/amazon/candidate/benefit_summary.aspx">Don't forget to utilize a benefit code if you've passed another AWS exam previously to save</a>

### Exam Content Breakdown:

| Domain  | % of Exam |
| ------------- | ------------- |
| Domain 1: Design Resilient Architectures | 34%  |
| Domain 2: Define Performant Architectures | 24%  |
| Domain 3: Specify Secure Applications and Architectures | 26% |
| Domain 4: Design Cost-Optimized Architectures  | 10% |
| Domain 5: Define Operationally Excellent Architectures  | 6% |
| **Total** | **100%** |

  * 170 minutes 
  * 65 questions
  * \>= 72% to pass
  * Good to use the bathroom before the exam
  * Average question time should be between 2 and 2 1/2 minutes
  * Try to understand each question thoroughly


# Sagemaker (SM)
## SM pipeline
  * name, steps, and parameters
  * designed to be scalable up to tens of thousands of ML workflows

## SM feature store 
  * off-line versus online
    
## SM script mode
  * run custom training script inside managed sage maker containers

## SM serverless inference

## SM experiments

## SM Canvas
  * Service for non-coders to build models
  * Doesn't provide comprehensive data preparation and transformations (if needed, use Data Wrangler)

## SM Data Wrangler
  * Provide comprehensive data preparation and transformations
  * Offers easy to use visual interface for data prep (e.g. cleaning transforming analyzing data) which is ideal for limited code use experience
  * Inputs
    * S3
    * Athena
    * Redshift
    * EMR
    * Lake formation (via Athena or AWS SDK awswrangler lib)
    * SM Feature Store
    * 3rd party sources (eg: Databricks, Snowflake Saas)
  * Outputs
    * S3
    * SM Processing
    * SM Pipelines
    * SM Feature Store
    * Autopilot
    * As a jupyter notebook
  * Does not integrate with DynamoDB

### SM Data Wrangler versus AWS Glue

## SM Categories of built-in algorithm:
  * supervised
  * unsupervised
  * textual analysis
  * image classification

## SM Algorithms
### Supervised vs Unsupervised Algorithms
  * Unsupervised:
    * Singular Value Decomposition (SVD)
    * Random Cut Forest
    * Neural Topic Model
    * LDA
    * K-Means
    * PCA
    * IP Insights
    * BlazingText (Word2vec)
  * Supervised:
    * Factorization Machines
    * KNN
    * Semantic Segmentation
    * Image Classification
    * Object Detection
    * Object2Vec
    * Deep AR Forecasting
    * Seq2Seq
    * BlazingText (Text Classification)
    * XGBoost
    * Linear Learner
    * Decision Trees
    * Naive Bayes
    * Logistic Regression
    * Recommendation Engine (ALS)
    * Support Vector Machine (SVM)
  * Neither: Reinforcement Learning

### Image classification
### XG boost
  * highly imbalanced data 
### Linear Learner
  * most effective approach to establish a simple, interpretable performance baseline to evaluate against more complex models in SM utilizing the same data

### linear learner versus XGBoost per class imbalance

# Data mesh architecture
  * data as a product with the decentralized data ownership and domain oriented architecture

# AWS Well-Architected Framework/Tool:

  * Pillars:
    * Operational excellence-run/monitor system/assets=>increase business value through RA/mitigation
    * Security-protect=>increase business value through RA/mitigation
    * Reliability-recover, dynamically allocate, mitigate despite misconfiguration/problem(s)
    * Performance-meet system requirements and maintenance through changes
    * Cost optimization-deliver at lowest price point
    * Sustainability-minimize environmental impact
  * Tool scans workloads for these criteria

# Kinesis
## kinesis producer Lib (KPL)
  * main advantage over custom AWS SDK coding: improved error handling and data throughput

## Kinesis data stream 
  * shard: a processing unit with a fixed data throughput capacity
## Amazon firehose
  # designed to deliver streaming data into AWS services (eg: S3, Redshift)

# EMR
## EMR cluster 
  * can use instance store for ephemeral/transient, cost-effective storage of temporary data
## EMR serverless

# Storage
## EBS
  * block level storage for raw storage(DB, or other)

## EFS
  * file storage

## FSX 
  * Mount versus linked

## S3

### standard versus intelligent tearing

## Database

### Redshift
  * data warehousing


# AWS Glue
  * glue partitioning aids parallel processing and boosts query performance
  * Inputs:
    * Aurora
    * Postgres, Redshift, SqlServer, Oracle, MySql (JDBC datastores) (RDS based or otherwise)
    * dynamodb
    * mongodb/documentdb
    * Kinesis Data Streams
    * Kafka/Amazon Managed Streaming for Apache Kafka
    * Athena
    * Spark
    * S3
    * Files (Orc, Parquet)
  * Outputs:
    * S3
    * JDBC (RDS, Redshift)
    * Glue Data Catalog
# Miscellaneous

## Load Balancers
  * Need both port 443 and 80 to be open with the latter being redirected to the former if enabled by the attachmment of an SSL certificate to the LB to allow the termination of HTTPS connections and thus serve secure content

## AWS Batch
  * Better matched over SM Batch jobs for extremely large, compute-intensive/high performance/scalable batch workloads 

## Catastrophic forgetting: when NNs abruptly lose previously learned information when trained on new, sequential data

## Feature selection versus model regularization

## L1 (LASSO) vs L2 (Ridge) Regularization
  * Preventing overfitting in ML in general
  * A regularization term is added as weights are learned
  * L1 term is the sum of the weights absolute weights
    * Performs feature selection - entire features go to O
    * Computationally inefficient
    * Sparse output
    * Good to avoid curse of dimensionality
    * When to use L1
      * Feature selection can reduce dimensionality
      * Out of 100 features, maybe only 10 end up with non-zero coefficients!
      * The resulting sparsity can make up for its computational inefficiency
      * But, if you think all of your features are important, L2 is probably a better choice.
  * L2 term is the sum of the square of the weights
    * All features remain considered, just weighted
    * Computationally efficient
    * Dense output
  * Same idea can be applied to loss functions and/or weights as learned
##R^2 (the coefficient of determination)
  * Indicate how much variance in the target (dependent) variable is explained by the independent variables of the model

# model overfitting
  * training and validation loss curves over time: if validation loss much higher than training loss-> model overfitting
##AWS CodePipeline
  * fully managed continuous delivery (CD) service that automates software release processes for fast and reliable updates

## Docker

## Athena
  * partition projection
## AWS CodeBuild
  * a fully managed continuous integration service that compiles source code, runs tests, and produces ready-to-deploy software packages
## Blue/Green Deployments
  * All at once: shift everything, monitor, terminate blue fleet
  * Canary: shift a small portion of traffic and monitor
  * Linear: Shift traffic in linearly spaced steps

# EC2
## EC2 Autoscaling
### schedule versus target tracking

## EC2 type suitability

## (Model) Stacking

# Amazon Translate
  * If small volumes of data, orchestrate via Lambda (15 minute limit)
  * If large volumes of data, orchestrate via step functions (up to 1 year limit)

# Shortcuts
  * 'manually' is usually a tell to not use the premise (eg: CPU/memory scaling doesn't necessarily help with manually scaled)
  * 'custom script' is a tell
