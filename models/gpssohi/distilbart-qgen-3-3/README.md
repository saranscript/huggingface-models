---
language: en
tags:
- question-generation
- summarization
license: apache-2.0
datasets:
- squad
---

# Introduction

This model checkpoint is obtained by first fine-tuning the sshleifer/distilbart-cnn-6-6 summarization checkpoint on the SQuAD dataset. After this, the 6-6 fine-tuned model is distilled down to a 3-3 model which gives us the final checkpoint. [GitHub Link for training scripts.](https://github.com/darth-c0d3r/bart-question-generation)

# Usage

The input format is as follows: `[answer] <s> [passage]`. The model will predict the question that corresponds to the answer from the passage.

# Plot

![Distillation Run](distill_run_21.png)

# Dataset

The goal of Question Generation is to generate a valid and fluent question according to a given passage and the target answer. Hence, the input to the model will be a passage context and an answer, and the output / target will be the question for the given answer. Question Generation can be used in many scenarios, such as automatic tutoring systems, improving the performance of Question Answering models and enabling chat-bots to lead a conversation. The final dataset is created by taking the union of the following Question Answering Datasets. The dataset must have the following three columns: context, question, answer.

## [SQuAD](https://rajpurkar.github.io/SQuAD-explorer/)

Stanford Question Answering Dataset (SQuAD) is a reading comprehension dataset, consisting of questions posed by crowd-workers on a set of Wikipedia articles, where the answer to every question is a segment of text, or span, from the corresponding reading passage, or the question might be unanswerable. We use the SQuAD 1.1 variant which does not have unanswerable questions. So, every question will have a corresponding answer and vice-versa.

### Preprocessing

The first step is to remove questions which don't have answers. After that, we split the train set into Train and Eval sets and treat the dev set as the test set.

### Stats

**Original Dataset**

| Split | Num Docs | Num Contexts | Ques w/ Ans | Ques w/o Ans | Num Unique Ans |
| ----- | -------- | ------------ | ----------- | ------------ | -------------- |
| Train | 442      | 19035        | 86821       | 43498        | 86821          |
| Dev   | 35       | 1204         | 5928        | 5945         | 10279          |

**After Preprocessing**

| Split | Num Rows |   Context  | Answer | Question |
| ----- | -------- | ---------- | ------ | -------- |
| Train | 80995    | 653,120,20 | 43,3,1 | 40,10,1  | 
| Eval  | 5826     | 445,123,67 | 28,3,1 | 29,10,3  |
| Test  | 10297    | 629,129,25 | 29,4,1 | 31,10,3  |

The numbers in the columns indicate max, avg, min number of words.
