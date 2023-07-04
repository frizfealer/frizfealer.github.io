# Designing Machine Learning Systems (1)


## Book Info

* Title: Designing Machine Learning Systems

* Author: Chip Huyen

* Publisher: O'Reilly

This is a reading note for this book.

## Chapter 1. Overview Of Machine Learning Systems

### Outline

1. When to use machine learning
2. Understanding machine learning systems
    1. Research vs production
    2. ML system vs traditional software system

### Recall

1. What are the different components of ML systems?
2. What does MLOps mean?  
3. What does a machine learning solution do?
4. What’s the difference between a traditional algorithm and an ML algorithm?
5. What are the cases where ML algorithms excel?
6. What are some customer ML applications?
7. The majority of ML use cases are still in the enterprise world. What are some enterprise ML applications?
8. What are the differences between research ML and production ML? Can answers from Requirements, Computational priority, data.
9. What are some criticisms of ML leaderboards? 
10. What does p99 mean in latency measurement?
11. In terms of system design, how is the ML system different from the traditional software system?

### Possible Answers to Recall

{{<admonition note answers >}}

1. What are the different components of ML systems?

    A: infrastructure, data, feature (engineering), ML algorithm, evaluation metrics, deployment, and monitoring continuous updates (CI/CD).

2. What does MLOps mean?  

    A: MLOps comes from DevOps, short for development and operations. To operate something means bringing it into production, which includes deploying, monitoring, and maintaining.

3. What does a machine learning solution do?

    A: An ML system learns complex patterns from data that can be used to make predictions on unseen data.

4. What’s the difference between a traditional algorithm and an ML algorithm?

    A: In the traditional algorithm, you code logic/patterns, whereas the ML algorithm, it learns logic/patterns from data.

5. What are the cases where ML algorithms excel?

    A: Wrong predictions are cheap, the ML system will be used a lot (at scale) because the development cost is high. Without ML you cannot do the task.

6. What are some customer ML applications?

    A: Recommendation, searching, face recognition. Text autocompletion.

7. The majority of ML use cases are still in the enterprise world. What are some enterprise ML applications?

    A: Fraud detection, price/cost optimization, demand forecasting, customer acquisition, churn prediction, and internal IT ticket routing predictions, brand monitoring.

8. What are the differences between research ML and production ML? Can answers from Requirements, Computational priority, data.

    A: 
    | Research | Research | Production |
    | --- | --- | --- |
    | Requirements | Achieve SOTA on public benchmark | Different stakeholders have different requirements |
    | Computational priority | Fast training, high throughput | Fast inference, low latency |
    | Data | Static, clean | Changing, dirty, need annotation. |
    | Others |  | Might need fairness, explainability |

9. What are some criticisms of ML leaderboards?

    A:
    1. Hard steps (collecting, cleaning, labeling) are already done for you. Recently data-centric ML, advocated by Andrew Ng has been a buzz term. 
    2. when you have multiple teams testing on the same hold-out test set, a model can do better than the rest just by chance. This is like you are reporting your evaluation number on the validation set ([ref](https://laurenoakdenrayner.com/2019/09/19/ai-competitions-dont-produce-useful-models/)).

10. What does p99 mean in latency measurement?

    A: p99 means the 99-percentile of your service latency. It is useful to check this number because it includes the most distribution of service latency.

11. In terms of system design, how is the ML system different from the traditional software system?

    A: In traditional SWE, code, and data are separated. Whereas in ML, code, data, and artifacts (model, features) are intertwined. In traditional SWE you versioned code. Whereas in ML, you might also version the data, and models. Large models with high complexity cause long computation times. Monitoring ML systems is harder because of the model's complexity. Cannot run parallelly for each component (model, features).
{{< /admonition >}}

### Summary
Machine learning (ML) systems can solve problems with complex patterns that are difficult to code. However, this comes at the price of a more complex data processing, service computation, and continuous integration/continuous deployment (MLOps). This chapter also covers common ML system use cases for both customers and enterprises. Finally, the chapter discusses the differences between ML in research and in production.

<br>

## Chapter 2. Introduction to Machine Learning Systems Design

### Outline

1. Business and ML Objective
2. Requirements of ML systems
3. The iterative development process of ML systems.
4. Framing ML problems
5. Mind versus data

### Good reference
[applied-ml: curated papers, articles, and blogs on data science & machine learning in production](https://github.com/eugeneyan/applied-ml)

### Recall

1. How to align Business and ML Objectives?
2. What are the four requirements of ML systems and what do they mean?
3. ML system development process involves many steps. What are they?
4. What are the different types of ML tasks?
5. How do you formulate multi-label ML tasks?
6. Whats the design strategy when you want to optimize multiple objectives of a ML algorithm?

### Possible Answers to Recall
{{<admonition note answers >}}

1. How to align Business and ML Objectives?

    A: Can be done in the following steps.
    1. Know what metrics business care about. e.g. sales: conversion rate.
    2. Tie the performance of an ML system to the overall business performance. You may need to conduct A/B tests to know how ML metrics influence business metrics.
    3. If the metrics of ML system and of the business are not aligned enough. Define custom ML metrics for better alignment, e.g. Netflix has take-rate: the number of quality plays divided by the number of recommendations a user sees.
2. What are the four requirements of ML systems and what do they mean?
    
    A:
    1. Reliability: The system should continue to
    perform the correct function at the desired level of performance even in the face of adversity. how do you measure the correctness of your model? (Using new test set, monitoring some metrics).
    2. Scalability

        | System Growth  | Solutions |
        | --- | --- |
        | parameters in models | distributed training |
        | traffic volume of service | auto-scaling |
        | many ML models | experiment and data version tracking |
    3. Maintainability: Code should be documented. Code, data, and artifacts should be versioned. ML engineers, subject matter experts, and software engineers can work together easily.
    4. Adaptability: the system should be adaptive to business requirement changes and data distribution changes.
3. ML system development process involves many steps. What are they?
    
    A: Project scoping, data engineering, model development, service deployment, monitoring and continuous learning, and business analysis.
4. What are the different types of ML tasks?
    
    A: Regression, classification(binary/multi-class (could be low or high cardinality), multi-label), recommendation.
5. How do you formulate multi-label ML tasks?

    A: You can formulate this into multiple binary classification problems. You can also formulate it as a multi-class classification.
6. Whats the design strategy when you want to optimize multiple objectives of a ML algorithm?

    A: You can have the objective function to be
    $$
    obj_{all} = \alpha obj_1 + \beta obj_2 + \dots
    $$
    if you want to systematically select alpha and beta, you can use pareto frontier. Any solution on the frontier cannot be improved in any of the objectives without degrading at least one of the other objectives.
    [multi-objective optimization from Wiki.](https://en.wikipedia.org/wiki/Multi-objective_optimization#/media/File:Front_pareto.svg)
    **However the book suggested another approach, that is having a model for each objective function. And you only tune each models output score when you want to weigh differently ,**
    $$
    score_{all} = \alpha score_1 + \beta score_2 + \dots
    $$
    Therefore, you don’t need to re-train the model because of different alpha and beta. This idea is like boosting!
{{< /admonition >}}

### Summary

The objective of machine learning (ML) systems should be driven by business needs since these systems are designed to serve business goals. ML systems should also have the same qualities as other software systems, such as reliability, scalability, maintainability, and adaptability (although the methods and metrics for achieving and measuring these qualities may differ from traditional software systems). Regression and classification are typical ML tasks. The book recommends training separate models for each objective function when we have multiple objectives to optimize and then combining their outputs with different weights. Finally, the book discusses some of the opinions of prominent AI experts on the trade-off between model and data.


---

> Author: Yeu-Chern Harn  
> URL: https://frizfealer.github.io/designing_machine_learning_systems_1/  

