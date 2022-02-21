[bioformer-cased-v1.0](https://huggingface.co/bioformers/bioformer-cased-v1.0) fined-tuned on the [SQuAD1](https://rajpurkar.github.io/SQuAD-explorer) dataset for 3 epochs.

The fine-tuning process was performed on a single P100 GPUs (16GB). The hyperparameters are:

```
max_seq_length=512
per_device_train_batch_size=16
gradient_accumulation_steps=1
total train batch size (w. parallel, distributed & accumulation) = 16
learning_rate=3e-5
num_train_epochs=3
```

## Evaluation results

```
"eval_exact_match": 78.55250709555345
"eval_f1": 85.91482799690257
```

Bioformer's performance is on par with [DistilBERT](https://arxiv.org/pdf/1910.01108.pdf) (EM/F1: 77.7/85.8), 
although Bioformer was pretrained only on biomedical texts. 


## Speed
In our experiments, the inference speed of Bioformer is 3x as fast as BERT-base/BioBERT/PubMedBERT, and is 40% faster than DistilBERT. 


