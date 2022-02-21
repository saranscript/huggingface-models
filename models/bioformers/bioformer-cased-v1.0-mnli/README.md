[bioformer-cased-v1.0](https://huggingface.co/bioformers/bioformer-cased-v1.0) fined-tuned on the [MNLI](https://cims.nyu.edu/~sbowman/multinli/) dataset for 2 epochs.

The fine-tuning process was performed on two NVIDIA GeForce GTX 1080 Ti GPUs (11GB). The parameters are:

```
max_seq_length=512
per_device_train_batch_size=16
total train batch size (w. parallel, distributed & accumulation) = 32
learning_rate=3e-5
```

## Evaluation results

eval_accuracy = 0.803973


## Speed

In our experiments, the inference speed of Bioformer is 3x as fast as BERT-base/BioBERT/PubMedBERT, and is 40% faster than DistilBERT. 

## More information
The Multi-Genre Natural Language Inference Corpus is a crowdsourced collection of sentence pairs with textual entailment annotations. Given a premise sentence and a hypothesis sentence, the task is to predict whether the premise entails the hypothesis (entailment), contradicts the hypothesis (contradiction), or neither (neutral). The premise sentences are gathered from ten different sources, including transcribed speech, fiction, and government reports. The authors of the benchmark use the standard test set, for which they obtained private labels from the RTE authors, and evaluate on both the matched (in-domain) and mismatched (cross-domain) section. They also uses and recommend the SNLI corpus as 550k examples of auxiliary training data. (source: https://huggingface.co/datasets/glue)