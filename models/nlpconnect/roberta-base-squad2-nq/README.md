---
tags:
- qa
license: apache-2.0
datasets:
- squad_v2
- natural_questions
---

# Roberta-base-Squad2-NQ

## What is SQuAD?
Stanford Question Answering Dataset (SQuAD) is a reading comprehension dataset, consisting of questions posed by crowdworkers on a set of Wikipedia articles, where the answer to every question is a segment of text, or span, from the corresponding reading passage, or the question might be unanswerable.

SQuAD2.0 combines the 100,000 questions in SQuAD1.1 with over 50,000 unanswerable questions written adversarially by crowdworkers to look similar to answerable ones. To do well on SQuAD2.0, systems must not only answer questions when possible, but also determine when no answer is supported by the paragraph and abstain from answering.

## The Natural Questions Dataset
To help spur development in open-domain question answering, we have created the Natural Questions (NQ) corpus, along with a challenge website based on this data. The NQ corpus contains questions from real users, and it requires QA systems to read and comprehend an entire Wikipedia article that may or may not contain the answer to the question. The inclusion of real user questions, and the requirement that solutions should read an entire page to find the answer, cause NQ to be a more realistic and challenging task than prior QA datasets.

## Training

Firstly, we took base roberta model and trained on SQuQD 2.0 dataset for 2 epoch and then after we took NQ Small answer and trained for 1 epoch.

Total Dataset Size: 204416 Examples from squadv2 and NQ Small answer dataset

## Evaluation

Eval Dataset: Squadv2 dev

```
  {'exact': 80.2998399730481,
   'f1': 83.4402145786235,
   'total': 11873,
   'HasAns_exact': 79.08232118758434,
   'HasAns_f1': 85.37207619635592,
   'HasAns_total': 5928,
   'NoAns_exact': 81.5138772077376,
   'NoAns_f1': 81.5138772077376,
   'NoAns_total': 5945,
   'best_exact': 80.2998399730481,
   'best_exact_thresh': 0.0,
   'best_f1': 83.44021457862335,
   'best_f1_thresh': 0.0}
 ```
 