## BERT-large finetuned on squad v2.

F1 on dev (from paper)[https://arxiv.org/pdf/1810.04805v2.pdf] is 81.9, we reach 81.58.

```
{'exact': 78.6321906847469,
'f1': 81.5816656803201,
'total': 11873,
'HasAns_exact': 73.73481781376518,
 'HasAns_f1': 79.64222615088413,
 'HasAns_total': 5928,
 'NoAns_exact': 83.51555929352396,
 'NoAns_f1': 83.51555929352396,
 'NoAns_total': 5945,
 'best_exact': 78.6321906847469,
 'best_exact_thresh': 0.0,
 'best_f1': 81.58166568032006,
 'best_f1_thresh': 0.0,
 'epoch': 1.59}
```


```
python run_qa.py \
  --model_name_or_path bert-large-uncased \
  --dataset_name squad_v2 \
  --do_train \
  --do_eval \
  --save_steps 2500 \
  --eval_steps 2500 \
  --evaluation_strategy steps \
  --per_device_train_batch_size 12 \
  --learning_rate 3e-5 \
  --num_train_epochs 2 \
  --max_seq_length 384 \
  --doc_stride 128 \
  --output_dir bert-large-uncased-squadv2 \
  --version_2_with_negative 1
  ```