This model is a downstream fine-tuning of [```vuiseng9/bert-base-squadv1-block-pruning-hybrid```](https://huggingface.co/vuiseng9/bert-base-squadv1-block-pruning-hybrid). "filled" means unstructured fine-grained sparsified parameters are allowed to learn during fine-tuning. "lt" means distillation of larger model as teacher, i.e. ```bert-large-uncased-whole-word-masking-finetuned-squad```  

```
  eval_exact_match = 80.3311
  eval_f1          = 87.69
  eval_samples     =   10784
``` 
This model is a replication of [block pruning paper](https://arxiv.org/abs/2109.04838) with its open-sourced codebase (forked and modified). 
To reproduce this model, pls follow [documentation here](https://github.com/vuiseng9/nn_pruning/blob/reproduce-evaluation/reproduce-eval/readme.md) until step 3.

# Eval
The model cannot be evaluated with HF QA example out-of-the-box as the final dimension of the model architecture has been realized. Follow the custom setup below.

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
This repo must be cloned locally.
```bash
git clone https://huggingface.co/vuiseng9/bert-base-squadv1-block-pruning-hybrid-filled-lt
```
Add ```--optimize_model_before_eval``` and ```--optimized_checkpoint /path/to/clone``` during evaluation.

```bash
export CUDA_VISIBLE_DEVICES=0

OUTDIR=eval-bert-base-squadv1-block-pruning-hybrid-filled-lt-cropped
WORKDIR=transformers/examples/pytorch/question-answering
cd $WORKDIR
mkdir $OUTDIR

nohup python run_qa.py  \
    --model_name_or_path vuiseng9/bert-base-squadv1-block-pruning-hybrid  \
    --dataset_name squad  \
    --optimize_model_before_eval \
    --optimized_checkpoint /path/to/clone/bert-base-squadv1-block-pruning-hybrid-filled-lt  \
    --do_eval  \
    --per_device_eval_batch_size 128  \
    --max_seq_length 384  \
    --doc_stride 128  \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```
