---
language: 
- bn
license: apache-2.0
tags:
- automatic-speech-recognition
- openslr_SLR53
- robust-speech-event
- bn
datasets:
- openslr
- SLR53
- AI4Bharat/IndicCorp
metrics:
- wer
- cer
model-index:
- name: arijitx/wav2vec2-xls-r-300m-bengali
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: openslr
      name: Open SLR
      args: SLR53
    metrics:
      - type: wer    # Required. Example: wer
        value: 0.21726385291857586  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
      - type: cer
        value: 0.04725010353701041
        name: Test CER
      - type: wer    # Required. Example: wer
        value:  0.15322879016421437  # Required. Example: 20.90
        name: Test WER with lm   # Optional. Example: Test WER
      - type: cer
        value: 0.03413696666806267
        name: Test CER with lm
---
This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the OPENSLR_SLR53 - bengali dataset.
It achieves the following results on the evaluation set. 

Without language model : 
- WER: 0.21726385291857586
- CER: 0.04725010353701041

With 5 gram language model trained on 30M sentences randomly chosen from [AI4Bharat IndicCorp](https://indicnlp.ai4bharat.org/corpora/) dataset : 
- WER: 0.15322879016421437
- CER: 0.03413696666806267

  

Note : 5% of a total 10935 samples have been used for evaluation. Evaluation set has 10935 examples which was not part of training training was done on first 95% and eval was done on last 5%. Training was stopped after 180k steps. Output predictions are available under files section.

### Training hyperparameters

The following hyperparameters were used during training:

- dataset_name="openslr"  	
- model_name_or_path="facebook/wav2vec2-xls-r-300m"  	
- dataset_config_name="SLR53"  	
- output_dir="./wav2vec2-xls-r-300m-bengali"  	
- overwrite_output_dir  	
- num_train_epochs="50"  	
- per_device_train_batch_size="32"  	
- per_device_eval_batch_size="32"  	
- gradient_accumulation_steps="1"  	
- learning_rate="7.5e-5"  	
- warmup_steps="2000"  	
- length_column_name="input_length"  	
- evaluation_strategy="steps"  	
- text_column_name="sentence"  	
- chars_to_ignore , ? . ! \- \; \: \" “ % ‘ ” � — ’ … –  	
- save_steps="2000"  	
- eval_steps="3000"  	
- logging_steps="100"  	
- layerdrop="0.0"  	
- activation_dropout="0.1"  	
- save_total_limit="3"  	
- freeze_feature_encoder  	
- feat_proj_dropout="0.0"  	
- mask_time_prob="0.75"  	
- mask_time_length="10"  	
- mask_feature_prob="0.25"  	
- mask_feature_length="64"      
- preprocessing_num_workers 32  

### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0

Notes
- Training and eval code modified from : https://github.com/huggingface/transformers/tree/master/examples/research_projects/robust-speech-event. 
- Bengali speech data was not available from common voice or librispeech multilingual datasets, so OpenSLR53 has been used.
- Minimum audio duration of 0.5s has been used to filter the training data which excluded may be 10-20 samples.
- OpenSLR53 transcripts are *not* part of LM training and LM used to evaluate.