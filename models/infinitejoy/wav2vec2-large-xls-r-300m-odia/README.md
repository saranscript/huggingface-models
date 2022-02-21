---
language:
- or
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- or
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Odia
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: or
    metrics:
       - name: Test WER
         type: wer
         value: 97.91
       - name: Test CER
         type: cer
         value: 247.09
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-odia

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - OR dataset.
It achieves the following results on the evaluation set:

```
python eval.py --model_id ./ --dataset mozilla-foundation/common_voice_7_0 --config as --split test --log_outputs
```

- WER: 1.0921052631578947
- CER: 2.5547945205479454

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

Training machine details

- Platform: Linux-5.11.0-37-generic-x86_64-with-glibc2.10
- CPU cores: 60
- Python version: 3.8.8
- PyTorch version: 1.10.1+cu102
- GPU is visible: True
- Transformers version: 4.16.0.dev0
- Datasets version: 1.17.1.dev0
- soundfile version: 0.10.3

Training script

```bash
python run_speech_recognition_ctc.py \
	--dataset_name="mozilla-foundation/common_voice_7_0" \
	--model_name_or_path="facebook/wav2vec2-xls-r-300m" \
	--dataset_config_name="or" \
	--output_dir="./wav2vec2-large-xls-r-300m-odia" \
	--overwrite_output_dir \
	--num_train_epochs="120" \
	--per_device_train_batch_size="16" \
	--per_device_eval_batch_size="16" \
	--gradient_accumulation_steps="2" \
	--learning_rate="7.5e-5" \
	--warmup_steps="500" \
	--length_column_name="input_length" \
	--evaluation_strategy="steps" \
	--text_column_name="sentence" \
	--chars_to_ignore , ? . ! \- \; \: \" “ % ‘ ” � — \’ … \– \' \’ \– \
	--save_steps="500" \
	--eval_steps="500" \
	--logging_steps="100" \
	--layerdrop="0.0" \
	--activation_dropout="0.1" \
	--save_total_limit="3" \
	--freeze_feature_encoder \
	--feat_proj_dropout="0.0" \
	--mask_time_prob="0.75" \
	--mask_time_length="10" \
	--mask_feature_prob="0.25" \
	--mask_feature_length="64" \
	--gradient_checkpointing \
	--use_auth_token \
	--fp16 \
	--group_by_length \
	--do_train --do_eval \
  --push_to_hub
```
    

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 120.0
- mixed_precision_training: Native AMP

### Training results

|    |   eval_loss |   eval_wer |   eval_runtime |   eval_samples_per_second |   eval_steps_per_second |   epoch |
|---:|------------:|-----------:|---------------:|--------------------------:|------------------------:|--------:|
|  0 |    3.35224  |   0.998972 |         5.0475 |                    22.189 |                   1.387 |   29.41 |
|  1 |    1.33679  |   0.938335 |         5.0633 |                    22.12  |                   1.382 |   58.82 |
|  2 |    0.737202 |   0.957862 |         5.0913 |                    21.998 |                   1.375 |   88.24 |
|  3 |    0.658212 |   0.96814  |         5.0953 |                    21.981 |                   1.374 |  117.65 |
|  4 |    0.658    |   0.9712   |         5.0953 |                    22.115 |                   1.382 |  120    |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
