This model is developed with transformers v4.13 with minor patch in this [fork](https://github.com/vuiseng9/transformers/tree/pegasus-v4p13).

# Setup
```bash
git clone https://github.com/vuiseng9/transformers
cd transformers
git checkout pegasus-v4p13 && git reset --hard 41eeb07
# installation, set summarization dependency
# . . .
```

# Train
```bash
#!/usr/bin/env bash

export CUDA_VISIBLE_DEVICES=0,1,2,3

NEPOCH=10
RUNID=pegasus-arxiv-${NEPOCH}eph-run1
OUTDIR=/data1/vchua/pegasus-hf4p13/pegasus-ft/${RUNID}
mkdir -p $OUTDIR

python run_summarization.py \
    --model_name_or_path google/pegasus-large \
    --dataset_name ccdv/arxiv-summarization \
    --do_train \
    --adafactor \
    --learning_rate 8e-4 \
    --label_smoothing_factor 0.1 \
    --num_train_epochs $NEPOCH \
    --per_device_train_batch_size 2 \
    --do_eval \
    --per_device_eval_batch_size 2 \
    --num_beams 8 \
    --max_source_length 1024 \
    --max_target_length 256 \
    --evaluation_strategy steps \
    --eval_steps 10000 \
    --save_strategy steps \
    --save_steps 5000 \
    --logging_steps 1 \
    --overwrite_output_dir \
    --run_name $RUNID \
    --output_dir $OUTDIR > $OUTDIR/run.log 2>&1 &
```

# Eval
```bash
#!/usr/bin/env bash

export CUDA_VISIBLE_DEVICES=3

DT=$(date +%F_%H-%M)
RUNID=pegasus-arxiv-${DT}
OUTDIR=/data1/vchua/pegasus-hf4p13/pegasus-eval/${RUNID}
mkdir -p $OUTDIR

python run_summarization.py \
    --model_name_or_path vuiseng9/pegasus-arxiv \
    --dataset_name ccdv/arxiv-summarization \
    --max_source_length 1024 \
    --max_target_length 256 \
    --do_predict \
    --per_device_eval_batch_size 8 \
    --predict_with_generate \
    --num_beams 8 \
    --overwrite_output_dir \
    --run_name $RUNID \
    --output_dir $OUTDIR > $OUTDIR/run.log 2>&1 &
```

Although fine-tuning is carried out for 5 epochs, this model is the checkpoint @150000 steps, 5.91 epoch, 34hrs) with lowest eval loss during training. Test/predict with this checkpoint should give results below. Note that we observe model at 80000 steps is closed to published result from HF.

```
***** predict metrics *****
  predict_gen_len            =   210.0925
  predict_loss               =     1.7192
  predict_rouge1             =    46.1383
  predict_rouge2             =    19.1393
  predict_rougeL             =    27.7573
  predict_rougeLsum          =     41.583
  predict_runtime            = 2:40:25.86
  predict_samples            =       6440
  predict_samples_per_second =      0.669
  predict_steps_per_second   =      0.084
```