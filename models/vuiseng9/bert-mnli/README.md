This model is developed with transformers v4.9.1.

```
  m             = 0.8444
  eval_samples  =   9815

  mm            = 0.8495
  eval_samples  =   9832
``` 

# Train
```bash
#!/usr/bin/env bash

export CUDA_VISIBLE_DEVICES=0

OUTDIR=bert-mnli
NEPOCH=3

WORKDIR=transformers/examples/pytorch/text-classification
cd $WORKDIR

python run_glue.py \
    --model_name_or_path bert-base-uncased \
    --task_name mnli \
    --max_seq_length 128 \
    --do_train \
    --per_device_train_batch_size 32 \
    --learning_rate 2e-5 \
    --num_train_epochs $NEPOCH \
    --logging_steps 1 \
    --evaluation_strategy steps \
    --save_steps 3000 \
    --do_eval \
    --per_device_eval_batch_size 128 \
    --eval_steps 250 \
    --output_dir $OUTDIR
    --overwrite_output_dir
```

# Eval
```bash
export CUDA_VISIBLE_DEVICES=0

OUTDIR=eval-bert-mnli
WORKDIR=transformers/examples/pytorch/text-classification
cd $WORKDIR

nohup python run_glue.py \
    --model_name_or_path vuiseng9/bert-mnli  \
    --task_name mnli  \
    --do_eval  \
    --per_device_eval_batch_size 128  \
    --max_seq_length 128  \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```
