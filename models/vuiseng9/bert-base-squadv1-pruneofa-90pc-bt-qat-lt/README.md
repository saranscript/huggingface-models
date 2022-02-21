This model is a downstream optimization of [```vuiseng9/bert-base-squadv1-pruneofa-90pc-bt```](https://huggingface.co/vuiseng9/bert-base-squadv1-pruneofa-90pc-bt) using [OpenVINO/NNCF](https://github.com/openvinotoolkit/nncf). Applied optimization includes:
1. magnitude sparsification at 0% upon initialization. Custom reverse masking and sparsity freezing are applied.
2. NNCF Quantize-Aware Training - Symmetric 8-bit for both weight and activation on all learnable layers.
3. Custom distillation with large model ```bert-large-uncased-whole-word-masking-finetuned-squad```  

```
  eval_exact_match = 80.6623
  eval_f1          = 87.7147
  eval_samples     =   10784
``` 


# Setup
```bash
# OpenVINO/NNCF
git clone https://github.com/vuiseng9/nncf && cd nncf
git checkout tld-poc
git reset --hard 5647610d5ee2bf9f1324604e6579bca1c391e260
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
git reset --hard 5dd7402e9a316041dea4ff67508c01047323616e
pip install -e .
head -n 1 examples/pytorch/question-answering/requirements.txt | xargs -i pip install {}

# Additional dependencies
pip install onnx
```

# Train

```bash
wget https://huggingface.co/vuiseng9/bert-base-squadv1-pruneofa-90pc-bt-qat-lt/raw/main/nncf_bert_squad_sparsity.json
NNCF_CFG=/path/to/downloaded_nncf_cfg_above #to-revise

OUTROOT=/path/to/train_output_root #to-revise
WORKDIR=transformers/examples/pytorch/question-answering #to-revise
RUNID=bert-base-squadv1-pruneofa-90pc-bt-qat-lt

cd $WORKDIR

OUTDIR=$OUTROOT/$RUNID
mkdir -p $OUTDIR

export CUDA_VISIBLE_DEVICES=0
NEPOCH=5

python run_qa.py \
    --model_name_or_path vuiseng9/bert-base-squadv1-pruneofa-90pc-bt \
    --pruneofa_qat \
    --dataset_name squad \
    --do_eval \
    --do_train \
    --evaluation_strategy steps \
    --eval_steps 250 \
    --learning_rate 3e-5 \
    --lr_scheduler_type cosine_with_restarts \
    --warmup_ratio 0.25 \
    --cosine_cycles 1 \
    --teacher bert-large-uncased-whole-word-masking-finetuned-squad \
    --teacher_ratio 0.9 \
    --num_train_epochs $NEPOCH \
    --per_device_eval_batch_size 128 \
    --per_device_train_batch_size 16 \
    --max_seq_length 384 \
    --doc_stride 128 \
    --save_steps 250 \
    --nncf_config $NNCF_CFG \
    --logging_steps 1 \
    --overwrite_output_dir \
    --run_name $RUNID \
    --output_dir $OUTDIR
```

# Eval
This repo must be cloned locally.
```bash
git clone https://huggingface.co/vuiseng9/bert-base-squadv1-pruneofa-90pc-bt-qat-lt
MODELROOT=/path/to/cloned_repo_above #to-revise

export CUDA_VISIBLE_DEVICES=0

OUTDIR=eval-bert-base-squadv1-pruneofa-90pc-bt-qat-lt
WORKDIR=transformers/examples/pytorch/question-answering #to-revise
cd $WORKDIR
mkdir $OUTDIR


nohup python run_qa.py  \
    --model_name_or_path vuiseng9/bert-base-squadv1-pruneofa-90pc-bt  \
    --dataset_name squad  \
    --qat_checkpoint $MODELROOT/checkpoint-22000  \
    --nncf_config $MODELROOT/nncf_bert_squad_sparsity.json  \
    --to_onnx $OUTDIR/bert-base-squadv1-pruneofa-90pc-bt-qat-lt.onnx  \
    --do_eval  \
    --per_device_eval_batch_size 128  \
    --max_seq_length 384  \
    --doc_stride 128  \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```
