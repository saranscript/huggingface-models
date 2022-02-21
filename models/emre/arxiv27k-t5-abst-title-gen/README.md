---
license: apache-2.0
tags:
- generated_from_trainer
- summarization
metrics:
- rouge
model-index:
- name: arxiv27k-t5-abst-title-gen/
  results: []
---

# arxiv27k-t5-abst-title-gen/

This model is a fine-tuned version of mt5-small on the arxiv-abstract-title dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6002
- Rouge1: 32.8
- Rouge2: 21.9
- Rougel: 34.8
- 

## Model description

Model has been trained with a colab-pro notebook in 4 hours.

## Intended uses & limitations

Can be used for generating journal titles from given abstracts

### Training args
model_args = T5Args()
model_args.max_seq_length = 256
model_args.train_batch_size = 8
model_args.eval_batch_size = 8
model_args.num_train_epochs = 6
model_args.evaluate_during_training = False
model_args.use_multiprocessing = False
model_args.fp16 = False
model_args.save_steps = 40000
model_args.save_eval_checkpoints = False
model_args.save_model_every_epoch = True
model_args.output_dir = OUTPUT_DIR
model_args.no_cache = True
model_args.reprocess_input_data = True
model_args.overwrite_output_dir = True
model_args.num_return_sequences = 1


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3

### Contact
detasar@gmail.com
Davut Emre Taşar