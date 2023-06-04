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
Machine learning (ML) systems can solve problems with complex patterns that are difficult to code. However, this comes at the price of a more complex data processing, service computation, and continuous integration/continuous deployment (MLOps). This chapter also covers common ML system use cases for both customers and enterprises. Finally, the chapter discusses the differences between ML in research and in production.**


---

> Author: Yeu-Chern Harn  
> URL: https://frizfealer.github.io/designing_machine_learning_systems_1/  

