---
language: no
license: cc-by-4.0
tags:
- seq2seq
datasets:
- Norwegian Nynorsk/Bokmål
---
# 🇳🇴 Norwegian T5 Base model Trained on the NCC🇳🇴  

This is a Norwegian T5-base model trained on the Norwegian Colossal Corpus (NCC) on a TPU v3-8. It needs to be finetuned on a specific task before being used for anything.

Currently the model is training. It is expected that it should be finished by the end of August 2021.

 The following setting were used in training:
```bash
 ./run_t5_mlm_flax.py \
    --output_dir="./" \
    --model_type="t5" \
    --config_name="./" \
    --tokenizer_name="./" \
    --train_file /mnt/disks/flaxdisk/corpus/norwegian_colossal_corpus_train.json \
    --validation_file /mnt/disks/flaxdisk/corpus/norwegian_colossal_corpus_validation.json \
    --max_seq_length="128" \
    --weight_decay="0.01" \
    --per_device_train_batch_size="128" \
    --per_device_eval_batch_size="128" \
    --learning_rate="8e-3" \
    --warmup_steps="2000" \
    --overwrite_output_dir \
    --cache_dir /mnt/disks/flaxdisk/cache/ \
    --num_train_epochs="3" \
    --adam_beta1="0.9" \
    --adam_beta2="0.98" \
    --logging_steps="100" \
    --save_steps="2500" \
    --eval_steps="2500" \
    --preprocessing_num_workers 96 \
    --adafactor \
    --push_to_hub
 ```