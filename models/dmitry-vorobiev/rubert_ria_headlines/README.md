---
language:
- ru
tags:
- summarization
- bert
- rubert
license: mit
---

# rubert_ria_headlines

## Description
*bert2bert* model, initialized with the `DeepPavlov/rubert-base-cased` pretrained weights and 
   fine-tuned on the first 99% of ["Rossiya Segodnya" news dataset](https://github.com/RossiyaSegodnya/ria_news_dataset) for 2 epochs.

## Usage example

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

MODEL_NAME = "dmitry-vorobiev/rubert_ria_headlines"

tokenizer = AutoTokenizer.from_pretrained(MODEL_NAME)
model = AutoModelForSeq2SeqLM.from_pretrained(MODEL_NAME)

text = "Скопируйте текст статьи / новости"

encoded_batch = tokenizer.prepare_seq2seq_batch(
    [text],
    return_tensors="pt",
    padding="max_length",
    truncation=True,
    max_length=512)

output_ids = model.generate(
    input_ids=encoded_batch["input_ids"],
    max_length=36,
    no_repeat_ngram_size=3,
    num_beams=5,
    top_k=0
)

headline = tokenizer.decode(output_ids[0], 
                            skip_special_tokens=True, 
                            clean_up_tokenization_spaces=False)
print(headline)
```
   
## Datasets
- [ria_news](https://github.com/RossiyaSegodnya/ria_news_dataset)

## How it was trained?

I used free TPUv3 on kaggle. The model was trained for 3 epochs with effective batch size 192 and soft restarts (warmup steps 1500 / 500 / 500 with new optimizer state on each epoch start).

- [1 epoch notebook](https://www.kaggle.com/dvorobiev/try-train-seq2seq-ria-tpu?scriptVersionId=53254694)
- [2 epoch notebook](https://www.kaggle.com/dvorobiev/try-train-seq2seq-ria-tpu?scriptVersionId=53269040)
- [3 epoch notebook](https://www.kaggle.com/dvorobiev/try-train-seq2seq-ria-tpu?scriptVersionId=53280797)

Common train params:

```shell
export XLA_USE_BF16=1
export XLA_TENSOR_ALLOCATOR_MAXSIZE=100000000

python nlp_headline_rus/src/train_seq2seq.py \
    --do_train \
    --tie_encoder_decoder \
    --max_source_length 512 \
    --max_target_length 32 \
    --val_max_target_length 48 \
    --tpu_num_cores 8 \
    --per_device_train_batch_size 24 \
    --gradient_accumulation_steps 1 \
    --learning_rate 5e-4 \
    --adam_epsilon 1e-6 \
    --weight_decay 1e-5 \
```

## Validation results

- Using [last 1% of ria](https://drive.google.com/drive/folders/1ztAeyb1BiLMgXwOgOJS7WMR4PGiI1q92) dataset
- Using [gazeta_ru test](https://drive.google.com/drive/folders/1CyowuRpecsLTcDbqEfmAvkCWOod58g_e) split
- Using [gazeta_ru val](https://drive.google.com/drive/folders/1XZFOXHSXLKdhzm61ceVLw3aautrdskIu) split