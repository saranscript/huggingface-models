---
license: apache-2.0
tags:
- generated_from_trainer
- gpt-neo

widget:
- text: "waddup bro?\n"  
  example_title: "waddup"
- text: "Are you going to be on League tonight?\n"  
  example_title: "League"
- text: "One of my hot takes is that dogs are cute. What do you think?\n"
  example_title: "hot take"
- text: "what planet is brandon from?\n"
  example_title: "brandon"
- text: "hello there.\n"
  example_title: "bold one"
inference:
  parameters:
    min_length: 2
    max_length: 64
    length_penalty: 0.6
    no_repeat_ngram_size: 2
    do_sample: True
    top_p: 0.97
    top_k: 30
    repetition_penalty: 5.2
    
---


# gpt-neo-125M-JIBA_DS-slack_Ep-40_Bs-8

This model is a fine-tuned version of [EleutherAI/gpt-neo-125M](https://huggingface.co/EleutherAI/gpt-neo-125M) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 7.0820

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

- while it would appear that over-fitting is a huge issue, the data is first sorted by the channel and then time, so the test set is a different channel than what is discussed during train and therefore it makes sense that the validation loss for a specific topic would increase during training. This doesn't exclude it from being a problem, but it is not immediately bad.
- this could be mitigated by stratifying the tokenized batches but because there are some intricacies, that was not completed for this MVP. If you are still reading this sentence you can do it though

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 4e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.05
- num_epochs: 40

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 190  | 4.0625          |
| No log        | 2.0   | 380  | 4.0195          |
| 3.9459        | 3.0   | 570  | 4.0078          |
| 3.9459        | 4.0   | 760  | 4.0117          |
| 3.9459        | 5.0   | 950  | 4.0352          |
| 3.5297        | 6.0   | 1140 | 4.0625          |
| 3.5297        | 7.0   | 1330 | 4.1094          |
| 3.2215        | 8.0   | 1520 | 4.1680          |
| 3.2215        | 9.0   | 1710 | 4.2305          |
| 3.2215        | 10.0  | 1900 | 4.3047          |
| 2.9058        | 11.0  | 2090 | 4.3906          |
| 2.9058        | 12.0  | 2280 | 4.4844          |
| 2.9058        | 13.0  | 2470 | 4.5977          |
| 2.5865        | 14.0  | 2660 | 4.6992          |
| 2.5865        | 15.0  | 2850 | 4.8125          |
| 2.2434        | 16.0  | 3040 | 4.9258          |
| 2.2434        | 17.0  | 3230 | 5.0391          |
| 2.2434        | 18.0  | 3420 | 5.1562          |
| 1.9185        | 19.0  | 3610 | 5.2773          |
| 1.9185        | 20.0  | 3800 | 5.3789          |
| 1.9185        | 21.0  | 3990 | 5.4961          |
| 1.6238        | 22.0  | 4180 | 5.5977          |
| 1.6238        | 23.0  | 4370 | 5.7109          |
| 1.3409        | 24.0  | 4560 | 5.8164          |
| 1.3409        | 25.0  | 4750 | 5.9023          |
| 1.3409        | 26.0  | 4940 | 5.9961          |
| 1.11          | 27.0  | 5130 | 6.0820          |
| 1.11          | 28.0  | 5320 | 6.1797          |
| 0.9143        | 29.0  | 5510 | 6.2539          |
| 0.9143        | 30.0  | 5700 | 6.3398          |
| 0.9143        | 31.0  | 5890 | 6.4258          |
| 0.7343        | 32.0  | 6080 | 6.5039          |
| 0.7343        | 33.0  | 6270 | 6.5859          |
| 0.7343        | 34.0  | 6460 | 6.6602          |
| 0.5904        | 35.0  | 6650 | 6.7305          |
| 0.5904        | 36.0  | 6840 | 6.7969          |
| 0.4654        | 37.0  | 7030 | 6.8711          |
| 0.4654        | 38.0  | 7220 | 6.9453          |
| 0.4654        | 39.0  | 7410 | 7.0156          |
| 0.3647        | 40.0  | 7600 | 7.0820          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Tokenizers 0.11.0
