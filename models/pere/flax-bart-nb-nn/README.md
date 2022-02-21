# RotoBART

## Running the script

### Script arguemnts

Available model config arguments from script:
```
encoder_layers
encoder_ffn_dim
decoder_layers
decoder_ffn_dim
d_model
vocab_size
max_position_embeddings
encoder_layerdrop
decoder_layerdrop
```

Training Arguments:

`testing` : only uses 1 batch, for testing the script

`adafactor`: will enable adafactor, removing the command will revert to Adam

`grad_accum`: what value for gradient accumulation to use, default is 4

`use_bf16`: convert the model to bf16

`colab_tpu`: if running on a colab TPU

`use_wandb`: log using Weights & Biases (via Tensorboard)

`save_strategy`: whether or not to save model checkpoints based on steps or epoch


```
python rotobart/run_dnlm_flax.py \
  --output_dir rotobart_output \
  --overwrite_output_dir \
  --dataset_path rotobart/pile.py \
  --model_name_or_path rotobart \
  --tokenizer_name ./rotobart/vocab-2/the_pile.model \
  --shuffle_buffer_size 1000 \
  --do_train --do_eval \
  --max_seq_length 1024 \
  --encoder_layers 2 \
  --decoder_layers 2 \
  --per_device_train_batch_size 2 \
  --per_device_eval_batch_size 2 \
  --logging_steps 8 \
  --num_train_steps 1000 \
  --eval_steps 1000 \
  --save_steps 1000 \
  --save_strategy steps \
  --num_eval_samples 100 \
  --warmup_steps 30 \
  --learning_rate 1e-4 \
  --use_wandb \
  --testing \
  --use_bf16 \
  --adafactor
```

alt

```
python3 run_dnlm_flax.py   --output_dir rotobart_output   --overwrite_output_dir   --dataset_path pile.py   --model_name_or_path rotobart   --tokenizer_name vocab-2/the_pile.model   --shuffle_buffer_size 1000   --do_train --do_eval --max_position_embeddings 2048  --max_seq_length 2048   --encoder_layers 6   --decoder_layers 6   --per_device_train_batch_size 1   --per_device_eval_batch_size 1   --logging_steps 100   --num_train_steps 50000   --eval_steps 2500   --save_steps 2500   --save_strategy steps   --num_eval_samples 5000   --warmup_steps 5000   --learning_rate 1e-4   --use_wandb   --use_bf16   --adafactor
```
