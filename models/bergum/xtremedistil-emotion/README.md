---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- emotion
metrics:
- accuracy
model-index:
- name: xtremedistil-emotion
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: emotion
      type: emotion
      args: default
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9265
---

# xtremedistil-emotion
This model is a fine-tuned version of [microsoft/xtremedistil-l6-h256-uncased](https://huggingface.co/microsoft/xtremedistil-l6-h256-uncased) on the emotion dataset.
It achieves the following results on the evaluation set:
- Accuracy: 0.9265


### Training hyperparameters
The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 128
- eval_batch_size: 8
- seed: 42
- num_epochs: 24

### Training results
<pre>
Epoch	Training Loss	Validation Loss	Accuracy
1	No log	1.238589	0.609000
2	No log	0.934423	0.714000
3	No log	0.768701	0.742000
4	1.074800	0.638208	0.805500
5	1.074800	0.551363	0.851500
6	1.074800	0.476291	0.875500
7	1.074800	0.427313	0.883500
8	0.531500	0.392633	0.886000
9	0.531500	0.357979	0.892000
10	0.531500	0.330304	0.899500
11	0.531500	0.304529	0.907000
12	0.337200	0.287447	0.918000
13	0.337200	0.277067	0.921000
14	0.337200	0.259483	0.921000
15	0.337200	0.257564	0.916500
16	0.246200	0.241970	0.919500
17	0.246200	0.241537	0.921500
18	0.246200	0.235705	0.924500
19	0.246200	0.237325	0.920500
20	0.201400	0.229699	0.923500
21	0.201400	0.227426	0.923000
22	0.201400	0.228554	0.924000
23	0.201400	0.226941	0.925500
24	0.184300	0.225816	0.926500
</pre>
