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
RUNID=pegasus-billsum-${NEPOCH}eph-run1
OUTDIR=/data1/vchua/pegasus-hf4p13/pegasus/${RUNID}
mkdir -p $OUTDIR

nohup python run_summarization.py \
    --model_name_or_path google/pegasus-large \
    --dataset_name billsum \
    --do_train \
    --adafactor \
    --learning_rate 2e-4 \
    --label_smoothing_factor 0.1 \
    --num_train_epochs $NEPOCH \
    --per_device_train_batch_size 2 \
    --do_eval \
    --per_device_eval_batch_size 2 \
    --num_beams 8 \
    --max_source_length 1024 \
    --max_target_length 256 \
    --evaluation_strategy steps \
    --eval_steps 1000 \
    --save_strategy steps \
    --save_steps 2000 \
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
RUNID=pegasus-billsum-${DT}
OUTDIR=/data1/vchua/pegasus-hf4p13/pegasus-test/${RUNID}
mkdir -p $OUTDIR

nohup python run_summarization.py \
    --model_name_or_path vuiseng9/pegasus-billsum \
    --dataset_name billsum \
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

Although fine-tuning is carried out for 10 epochs, this model is the checkpoint (@12000 steps, 6.6epoch, 210mins) with lowest eval loss during training. Test/predict with this checkpoint should give results below.

```
***** predict metrics *****
  predict_gen_len            =   179.7363
  predict_loss               =     1.2452
  predict_rouge1             =    56.8657
  predict_rouge2             =    38.6531
  predict_rougeL             =    44.8399
  predict_rougeLsum          =    51.6266
  predict_runtime            = 1:19:28.20
  predict_samples            =       3269
  predict_samples_per_second =      0.686
  predict_steps_per_second   =      0.086
```