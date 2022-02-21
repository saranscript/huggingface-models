This model is developed with transformers v4.10.3.

# Train
```bash
#!/usr/bin/env bash

export CUDA_VISIBLE_DEVICES=0

OUTDIR=bert-base-uncased-squad
WORKDIR=transformers/examples/pytorch/question-answering
cd $WORKDIR

nohup python run_qa.py \
    --model_name_or_path bert-base-uncased \
    --dataset_name squad \
    --do_eval \
    --do_train \
    --per_device_train_batch_size 16 \
    --per_device_eval_batch_size 16 \
    --doc_stride 128 \
    --max_seq_length 384 \
    --learning_rate 3e-5 \
    --num_train_epochs 2 \
    --eval_steps 250 \
    --save_steps 2500 \
    --logging_steps 1 \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```

# Eval
```bash
export CUDA_VISIBLE_DEVICES=0

OUTDIR=eval-bert-base-uncased-squad
WORKDIR=transformers/examples/pytorch/question-answering
cd $WORKDIR

nohup python run_qa.py  \
    --model_name_or_path vuiseng9/bert-base-uncased-squad  \
    --dataset_name squad  \
    --do_eval  \
    --per_device_eval_batch_size 16  \
    --max_seq_length 384  \
    --doc_stride 128  \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```
