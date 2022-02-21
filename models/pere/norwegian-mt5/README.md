---
language: no
license: cc-by-4.0
tags:
- seq2seq
datasets:
- Norwegian Nynorsk/BokmÃ¥l
---
#  🇳🇴 Norwegian mT5 Base model 🇳🇴
This mT5-base model is trained from the mT5 checkpoint on a 19GB Balanced Bokmål-Nynorsk Corpus.

Parameters used in training:
```bash
python3 ./run_t5_mlm_flax_streaming.py 
    --model_name_or_path="./norwegian-t5-base"
    --output_dir="./norwegian-t5-base" 
    --config_name="./norwegian-t5-base" 
    --tokenizer_name="./norwegian-t5-base" 
    --dataset_name="pere/nb_nn_balanced_shuffled"  
    --max_seq_length="512" 
    --per_device_train_batch_size="32" 
    --per_device_eval_batch_size="32" 
    --learning_rate="0.005" 
    --weight_decay="0.001" 
    --warmup_steps="2000" 
    --overwrite_output_dir  
    --logging_steps="100" 
    --save_steps="500" 
    --eval_steps="500"
    --push_to_hub 
    --preprocessing_num_workers 96 
    --adafactor 
  ```