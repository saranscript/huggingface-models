---
language: en
license: mit
datasets:
- conll2003
widget:
- text: My name is Clara Clever and I live in Berkeley , California .
---

# T5 Base Model for Named Entity Recognition (NER, CoNLL-2003)

In this repository, we open source a T5 Base model, that was fine-tuned on the official CoNLL-2003 NER dataset.

We use the great [TANL library](https://github.com/amazon-research/tanl) from Amazon for fine-tuning the model.

The exact approach of fine-tuning is presented in the "TANL: Structured Prediction as Translation between Augmented Natural Languages"
paper from Giovanni Paolini, Ben Athiwaratkun, Jason Krone, Jie Ma, Alessandro Achille, Rishita Anubhai, Cicero Nogueira dos Santos, Bing Xiang and Stefano Soatto.

# Fine-Tuning

We use the same hyper-parameter settings as used in the official implementation with one minor change. Instead of using 8 V100 GPUs, we train the model
on one V100 GPU and used gradient accumulation. The slighly modified configuration file (`config.ini`) then looks like:

```ini
[conll03]
datasets = conll03
model_name_or_path = t5-base
num_train_epochs = 10
max_seq_length = 256
max_seq_length_eval = 512
per_device_train_batch_size = 4
per_device_eval_batch_size = 4
do_train = True
do_eval = True
do_predict = True
gradient_accumulation_steps = 8
```

It took around 2 hours to fine-tune that model on the 14,041 training sentences of CoNLL-2003 dataset.

# Evaluation

On the development set, the following evaluation results could be achieved:

```json
{
"entity_precision": 0.9536446086664427,
"entity_recall": 0.9555705149781218,
"entity_f1": 0.9546065904505716,
"entity_precision_no_type": 0.9773261672824992,
"entity_recall_no_type": 0.9792998990238977,
"entity_f1_no_type": 0.9783120376597176
}
```

The evaluation results on the test set looks like:

```json
{
"entity_precision": 0.912182296231376,
"entity_recall": 0.9213881019830028,
"entity_f1": 0.9167620893155995,
"entity_precision_no_type": 0.953900087642419,
"entity_recall_no_type": 0.9635269121813032,
"entity_f1_no_type": 0.9586893332158901
}
```

To summarize: On the development set, 95.46% F1-Score and 91.68% on test set were achieved with this model. The paper reported a F1-Score of 91.7%.

# License

The models is licensed under [MIT](https://choosealicense.com/licenses/mit/).

# Acknowledgments

Thanks to the generous support from the [Hugging Face](https://huggingface.co/) team,
it is possible to download both cased and uncased models from their S3 storage 🤗
