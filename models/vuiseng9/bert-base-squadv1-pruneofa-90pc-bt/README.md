This model is transfer-learning of [bert-base pruneofa 90% sparse](https://huggingface.co/Intel/bert-base-uncased-sparse-90-unstructured-pruneofa) on Squadv1 dataset.

```
  eval_exact_match = 80.2933
  eval_f1          = 87.6788
  eval_samples     =   10784
``` 


# Train
use https://github.com/IntelLabs/Model-Compression-Research-Package.git
see ```pruneofa-transfer-learning.sh```

# Eval
```bash
export CUDA_VISIBLE_DEVICES=0

OUTDIR=eval-bert-base-squadv1-pruneofa-90pc-bt
WORKDIR=transformers/examples/pytorch/question-answering
cd $WORKDIR

nohup python run_qa.py  \
    --model_name_or_path vuiseng9/bert-base-squadv1-pruneofa-90pc-bt  \
    --dataset_name squad  \
    --do_eval  \
    --per_device_eval_batch_size 128  \
    --max_seq_length 384  \
    --doc_stride 128  \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```
