This model is developed with transformers v4.13 with minor patch in this [fork](https://github.com/vuiseng9/transformers/tree/pegasus-v4p13).

# Setup
```bash
git clone https://github.com/vuiseng9/transformers
cd transformers
git checkout pegasus-v4p13 && git reset --hard 3db4b452
# installation, set summarization dependency
# . . .
```

# Train
```bash
#!/usr/bin/env bash

export CUDA_VISIBLE_DEVICES=0,1 # 2 cards on xsum

NEPOCH=10
RUNID=pegasus-xsum-${NEPOCH}eph-run1
OUTDIR=/data1/vchua/pegasus-hf4p13/pegasus/${RUNID}
mkdir -p $OUTDIR

nohup python run_summarization.py \
    --model_name_or_path google/pegasus-large \
    --dataset_name xsum \
    --do_train \
    --adafactor \
    --learning_rate 1e-4 \
    --label_smoothing_factor 0.1 \
    --num_train_epochs $NEPOCH \
    --per_device_train_batch_size 8 \
    --do_eval \
    --per_device_eval_batch_size 8 \
    --num_beams 8 \
    --max_source_length 512 \
    --max_target_length 64 \
    --evaluation_strategy steps \
    --eval_steps 1000 \
    --save_strategy steps \
    --save_steps 2000 \
    --logging_steps 1 \
    --overwrite_output_dir \
    --run_name $RUNID \
    --output_dir $OUTDIR > $OUTDIR/run.log 2>&1
```

# Eval
```bash
#!/usr/bin/env bash

export CUDA_VISIBLE_DEVICES=3

DT=$(date +%F_%H-%M)
RUNID=pegasus-xsum-${DT}
OUTDIR=/data1/vchua/pegasus-hf4p13/pegasus-test/${RUNID}
mkdir -p $OUTDIR

nohup python run_summarization.py \
    --model_name_or_path vuiseng9/pegasus-xsum \
    --dataset_name xsum \
    --max_source_length 512 \
    --max_target_length 64 \
    --do_predict \
    --per_device_eval_batch_size 16 \
    --predict_with_generate \
    --num_beams 8 \
    --overwrite_output_dir \
    --run_name $RUNID \
    --output_dir $OUTDIR > $OUTDIR/run.log 2>&1 &
```

Although fine-tuning is carried out for 10 epochs, this model is the checkpoint (@62000 steps, 4.9epoch, 20hrs) with lower loss during training. Test/predict with this checkpoint should give results below.

```
***** predict metrics *****
  predict_gen_len            =    24.0499
  predict_loss               =     1.5801
  predict_rouge1             =    47.2124
  predict_rouge2             =    24.3673
  predict_rougeL             =    39.0055
  predict_rougeLsum          =    39.0007
  predict_runtime            = 0:34:23.32
  predict_samples            =      11334
  predict_samples_per_second =      5.493
  predict_steps_per_second   =      0.344
```