This model is developed with transformers v4.10.3.

# Train
```bash
#!/usr/bin/env bash

export CUDA_VISIBLE_DEVICES=0

OUTDIR=bert-based-uncased-mnli
WORKDIR=transformers/examples/pytorch/text-classification
cd $WORKDIR

nohup python run_glue.py \
    --model_name_or_path bert-base-uncased  \
    --task_name mnli  \
    --do_eval  \
    --do_train  \
    --per_device_train_batch_size 16  \
    --per_device_eval_batch_size 16  \
    --max_seq_length 128  \
    --num_train_epochs 3 \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```

# Eval
```bash
export CUDA_VISIBLE_DEVICES=0

OUTDIR=eval-bert-based-uncased-mnli
WORKDIR=transformers/examples/pytorch/text-classification
cd $WORKDIR

nohup python run_glue.py \
    --model_name_or_path vuiseng9/bert-base-uncased-mnli  \
    --task_name mnli  \
    --do_eval  \
    --per_device_eval_batch_size 16  \
    --max_seq_length 128  \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```
