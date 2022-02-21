**[`microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext`](https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext)** fine-tuned on **[`SQuAD V2`](https://rajpurkar.github.io/SQuAD-explorer/)** using **[`run_qa.py`](https://github.com/huggingface/transformers/blob/master/examples/pytorch/question-answering/run_qa.py)**

Tunning script:
```bash
BASE_MODEL=microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext
OUTPUT_DIR=~/Documents/projects/tunned_models/ms_pubmed_bert_squadv2/

python run_qa.py \
  --model_name_or_path  $BASE_MODEL\
  --dataset_name squad_v2 \
  --do_train \
  --do_eval \
  --version_2_with_negative \
  --per_device_train_batch_size 12 \
  --learning_rate 3e-5 \
  --num_train_epochs 2 \
  --max_seq_length 384 \
  --doc_stride 128 \
  --output_dir $OUTPUT_DIR
```