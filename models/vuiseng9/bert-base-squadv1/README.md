This model is a fork of [```csarron/bert-base-uncased-squad-v1```](https://huggingface.co/csarron/bert-base-uncased-squad-v1).

```
  eval_exact_match = 80.9082
  eval_f1          = 88.2275
  eval_samples     =   10784
``` 

# Eval
```bash
export CUDA_VISIBLE_DEVICES=0

OUTDIR=eval-bert-base-squadv1
WORKDIR=transformers/examples/pytorch/question-answering
cd $WORKDIR

nohup python run_qa.py  \
    --model_name_or_path vuiseng9/bert-base-squadv1  \
    --dataset_name squad  \
    --do_eval  \
    --per_device_eval_batch_size 128  \
    --max_seq_length 384  \
    --doc_stride 128  \
    --overwrite_output_dir \
    --output_dir $OUTDIR 2>&1 | tee $OUTDIR/run.log &
```
