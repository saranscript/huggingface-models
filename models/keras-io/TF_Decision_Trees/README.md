￼
---
language: 
  - en

thumbnail: 
tags:
- classification
- gradient boosted trees
- keras
- TensorFlow

license: apache-2.0

libraries: TensorBoard

metrics:
- accuracy

model-index:
- name: TF_Decision_Trees
  results:
  - task: 
      type: structured-data-classification
      name: Structured Data Classification
    dataset:
      type: census
      name: Census-Income Data Set
    metrics:
    - type: accuracy
      value: 96.57
      
pipeline_tag: "structured-data-classification"
---

# Classification with TensorFlow Decision Forests 

#### Using TensorFlow Decision Forests for structured data classification
 <br />

##### This example uses Gradient Boosted Trees model in binary classification of structured data, and covers the following scenarios:


1. Build a decision forests model by specifying the input feature usage.

2. Implement a custom Binary Target encoder as a Keras Preprocessing layer to encode the categorical features with respect to their target value co-occurrences, and then use the encoded features to build a decision forests model.

The example uses Tensorflow 7.0 or higher. It uses the US Census Income Dataset containing approximately 300k instances with 41 numerical and categorical variables. This is a binary classification problem to determine whether a person makes over 50k a year. 


Author: Khalid Salama  <br /> 

Adapted implementation: Tannia Dubon
