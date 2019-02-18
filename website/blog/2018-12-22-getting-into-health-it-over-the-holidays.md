---
title: Getting into healthcare it over the holidays
author: Den
authorURL: http://twitter.com/denseidel
authorFBID: 1440692838
---

Welcome to my journey learning the essentials to build a product in the the healthcare domain. I will start by learning the principles about product design and bootstraping a product, and will continue with the implementation as well as legal aspects.

For years I wanted to contribute to the healthcare domain. But it never fitted my job role, I never had time and overall where missing some skill. This holidays I decided to change this and get started with this step by step and document this here. 

## The Goal - is to learn the fundamentals

Frameworks & tools change rapidly, the fundamentals don't [[1](https://sizovs.net/2018/12/17/stop-learning-frameworks/)]. Therefore I split my time 80% on learning the fundamentals and 20% working on the project. This will include:

| Fundamentals                     | Framework                  |
| -------------------------------- | -------------------------- |
| Product Design                   | Lean Startup               |
| Evolutionary Architecture        | Microservices frameworks   |
| Clean Code, Design Patterns, DDD | New programming language   |
| Lean manufacturing principles    | LeSS, SAFe                 |
| Fault Tolerance Patterns         | Hystrix                    |
| Continuous Delivery              | Docker                     |
| Web, HTTP and REST               | Angular / React            |
| Machine Learning                 | PyTorch, Tensorflow        |
| Data Science Process             | Kaggle, Pipeline Tool      |
| Genomics                         | Genomics Library Framework |

I will sumarize what I *learned* and *build* in a blog post and present it in short video blogs. 

## The project outline

The goal of the project is to **build a product in the healthcare domain (e.g. a multi tenent analytics platform for healthcare insurances)** and document the process so it can be applied to other domains. 

| Goal                                                                 | Fundamentals                                                                        | Framework                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Design the product                                                   | [Product Design/UI principles](https://eu.udacity.com/course/product-design--ud509) | Framework: Sketch? Mocketo?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Design the architecture                                              | DDD, Evolutionary architecture                                                      | UML, Event Storming, ADRs, [SaaS Design on AWS](https://www.youtube.com/watch?v=kmVUbngCyOw)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Setup the infrastructure: Cloud Accounts, Toolstack, DevOps Pipeline | Continous Delivery                                                                  | CircleCI, Docker, [Serverless CI/CD](https://serverless.com/blog/ci-cd-workflow-serverless-apps-with-circleci/)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Design the services (README) and Implement it                        | Clean Code, Design Patterns, DDD                                                    | Python, NodeJS/Express, [Serverless](https://serverless-stack.com/), [Portable Serverless](https://hackernoon.com/deploy-a-serverless-flask-application-on-aws-lambda-d8ca58af42a4)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Build the app logic (machine learning model)                         | Machine Learning, Artifical Intelligence                                            | Kaggle, Python/Pandas, PyTorch, [Fast.AI](https://course.fast.ai/lessons/lesson1.html) / [Fast.AI on Kaggle](https://towardsdatascience.com/announcing-fast-ai-part-1-now-available-as-kaggle-kernels-8ef4ca3b9ce6) / [Kaggle Learn](https://www.kaggle.com/learn/overview) / [Bloomberg - Machine Learning](https://bloomberg.github.io/foml/#home) / [Histopathologic Cancer Detection Challange](https://www.kaggle.com/c/histopathologic-cancer-detection) / Solution:  [Fast.AI](https://www.kaggle.com/qitvision/a-complete-ml-pipeline-fast-ai/notebook) / [Other](https://towardsdatascience.com/histopathologic-cancer-detector-finding-cancer-cells-with-machine-learning-b77ce1ee9b0a) / [Skin cancer classification](https://hackernoon.com/machine-learning-for-isic-skin-cancer-classification-challenge-part-1-ccddea4ec44a) / [Stratified Healthcare / Kaggle Challange](https://www.kaggle.com/c/msk-redefining-cancer-treatment) / [Human Protein Atlas / Kaggle](https://www.kaggle.com/c/human-protein-atlas-image-classification/discussion/73938) / [Python Tinder API](https://github.com/charliewolf/pynder) / [Automate tinder](https://towardsdatascience.com/m2m-day-89-how-i-used-artificial-intelligence-to-automate-tinder-ced91b947e53) / [tinder - deep learning](http://philipperemy.github.io/tinder-deep-learning/) / [Tinder Analysis by a woman](https://medium.com/@lisachen_7431/of-machine-learning-and-men-a-brief-analysis-of-my-tinder-data-47cb849c963f) |
| Build a data pipeline                                                |                                                                                     | [Acumos Marketplace](https://acumos.org)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Design an data lake                                                  |                                                                                     | [AWS Datalake](https://aws.amazon.com/lake-formation/)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Expose the machine learning model as a service                       |                                                                                     | protobuffer like in acumos pipelines / [Google Vision API](https://cloud.google.com/vision/) / [Architecture](https://cloud.google.com/images/products/vision/image-search.svg)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Ensure data security for insurance and healthcare on the platform    | Encryption, Legal Requirements (as the startup and the legal/secs at work)          | [AWS KMS](https://aws.amazon.com/blogs/security/are-kms-custom-key-stores-right-for-you/) / How let the saas user manage the key and get a temporary key for e.g. 24 hours that he can send to us?                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Build a billing system                                               |                                                                                     | Swipe, AWS Marketpalce                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Span the application accross multiple clouds                         |                                                                                     | how one would implement a token manager in polycloud (one token manager per cloud?)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

## What is next? 

**Product Design:** The next post give you a summary about what I learned and how I applied it. 