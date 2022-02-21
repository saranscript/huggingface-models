## Roberta-Large

This repo trains [roberta-large](https://huggingface.co/roberta-large) from scratch on the [Norwegian training subset of Oscar](https://oscar-corpus.com/) containing roughly 4.7 GB of data.

A ByteLevelBPETokenizer as shown in [this]( ) blog post was trained on the whole [Norwegian training subset of Oscar](https://oscar-corpus.com/).

Training is done on a TPUv3-8 in Flax. The training script as well as the script to create a tokenizer are attached below.

### Run 1

```
--weight_decay="0.01"
--max_seq_length="128"
--train_batch_size="1048"
--eval_batch_size="1048"
--learning_rate="1e-3"
--warmup_steps="2000"
--pad_to_max_length
--num_train_epochs="12"
--adam_beta1="0.9"
--adam_beta2="0.98"
```

Trained for 12 epochs with each epoch including 8005 steps => Total of 96K steps. 1 epoch + eval takes roughly 2 hours 40 minutes => trained in total for 1 day and 8 hours. Final loss was 3.695.

**Acc**:

![Acc](https://raw.githubusercontent.com/patrickvonplaten/scientific_images/master/flax_experiments/norwegian_large_acc_1.svg)

**Loss**:

![Loss](https://raw.githubusercontent.com/patrickvonplaten/scientific_images/master/flax_experiments/norwegian_large_loss_1.svg)

### Run 2

```
--weight_decay="0.01"
--max_seq_length="128"
--train_batch_size="1048"
--eval_batch_size="1048"
--learning_rate="5e-3"
--warmup_steps="2000"
--pad_to_max_length
--num_train_epochs="7"
--adam_beta1="0.9"
--adam_beta2="0.98"
```

Trained for 7 epochs with each epoch including 8005 steps => Total of 96K steps. 1 epoch + eval takes roughly 2 hours 40 minutes => trained in total for 18 hours. Final loss was 2.216 and accuracy 0.58.


**Acc**:

![Acc](https://raw.githubusercontent.com/patrickvonplaten/scientific_images/master/flax_experiments/norwegian_large_acc_2.svg)

**Loss**:

![Loss](https://raw.githubusercontent.com/patrickvonplaten/scientific_images/master/flax_experiments/norwegian_large_loss_2.svg)
