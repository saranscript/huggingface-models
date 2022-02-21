BERT-base tuned for Squadv1.1 is pruned with movement pruning algorithm in hybrid fashion, i.e. 32x32 block for self-attention layers, per-dimension grain size for ffn layers.
```
  eval_exact_match = 78.5241
  eval_f1          = 86.4138
  eval_samples     =   10784
``` 
This model is a replication of [block pruning paper](https://arxiv.org/abs/2109.04838) with its open-sourced codebase (forked and modified). 
To reproduce this model, pls follow [documentation here](https://github.com/vuiseng9/nn_pruning/blob/reproduce-evaluation/reproduce-eval/readme.md) until step 2.

# Eval
The model can be evaluated out-of-the-box with HF QA example. Note that only pruned self-attention heads are discarded where pruned ffn dimension are sparsified instead of removal. Verified in v4.13.0, v4.9.1.
```bash
export CUDA_VISIBLE_DEVICES=0

OUTDIR=eval-bert-base-squadv1-block-pruning-hybrid
WORKDIR=transformers/examples/pytorch/question-answering
cd $WORKDIR
mkdir $OUTDIR

nohup python run_qa.py  \
    --model_name_or_path vuiseng9/bert-base-squadv1-block-pruning-hybrid  \
    --dataset_name squad  \
    --do_eval  \
    --per_device_eval_batch_size 16  \
    --max_seq_length 384  \
    --doc_stride 128  \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```

If the intent is to observe inference acceleration, the pruned structure in the model must be "cropped"/discarded. Follow the custom setup below.
```bash
# OpenVINO/NNCF
git clone https://github.com/vuiseng9/nncf && cd nncf
git checkout tld-poc
git reset --hard 1dec7afe7a4b567c059fcf287ea2c234980fded2
python setup.py develop
pip install -r examples/torch/requirements.txt

# Huggingface nn_pruning
git clone https://github.com/vuiseng9/nn_pruning && cd nn_pruning
git checkout reproduce-evaluation
git reset --hard 2d4e196d694c465e43e5fbce6c3836d0a60e1446
pip install -e ".[dev]"

# Huggingface Transformers
git clone https://github.com/vuiseng9/transformers && cd transformers
git checkout tld-poc
git reset --hard 10a1e29d84484e48fd106f58957d9ffc89dc43c5
pip install -e .
head -n 1 examples/pytorch/question-answering/requirements.txt | xargs -i pip install {}

```
Add ```--optimize_model_before_eval``` during evaluation.
```bash
export CUDA_VISIBLE_DEVICES=0

OUTDIR=eval-bert-base-squadv1-block-pruning-hybrid-cropped
WORKDIR=transformers/examples/pytorch/question-answering
cd $WORKDIR
mkdir $OUTDIR

nohup python run_qa.py  \
    --model_name_or_path vuiseng9/bert-base-squadv1-block-pruning-hybrid  \
    --dataset_name squad  \
    --optimize_model_before_eval \
    --do_eval  \
    --per_device_eval_batch_size 128  \
    --max_seq_length 384  \
    --doc_stride 128  \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```
