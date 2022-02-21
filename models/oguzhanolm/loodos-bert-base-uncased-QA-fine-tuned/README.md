---
language: tr
tags:
- question-answering
- loodos-bert-base
- TQuAD 
- tr
datasets:
- TQuAD
model-index:
- name: loodos-bert-base-uncased-QA-fine-tuned
  results: 
  - task:
      name: Question Answering
      type: question-answering
    dataset:
      name: TQuAD
      type: question-answering
      args: tr
    metrics:
      - name: Accuracy 
        type: acc
        value: 0.91
---

# Turkish SQuAD  Model : Question Answering

I fine-tuned Loodos-Turkish-Bert-Model for Question-Answering problem with TQuAD dataset
* Loodos-BERT-base: https://huggingface.co/loodos/bert-base-turkish-uncased
* TQuAD dataset:  https://github.com/TQuad/turkish-nlp-qa-dataset


# Training Code

```
!python3 Turkish-QA.py \
  --model_type bert \
  --model_name_or_path loodos/bert-base-turkish-uncased
  --do_train \
  --do_eval \
  --train_file trainQ.json \
  --predict_file dev1.json \
  --per_gpu_train_batch_size 8 \
  --learning_rate 5e-5 \
  --num_train_epochs 6 \
  --max_seq_length 384 \
  --output_dir "./model"
```

# Example Usage

> Load Model
```
from transformers import AutoTokenizer, AutoModelForQuestionAnswering

tokenizer = AutoTokenizer.from_pretrained("oguzhanolm/loodos-bert-base-uncased-QA-fine-tuned")

model = AutoModelForQuestionAnswering.from_pretrained("oguzhanolm/loodos-bert-base-uncased-QA-fine-tuned")

nlp = pipeline('question-answering', model=model, tokenizer=tokenizer)
```

> Apply the model
```
def ask(question,context):
  temp = nlp(question=question, context=context)
  start_idx = temp["start"]
  end_idx = temp["end"]
  return context[start_idx:end_idx]

istanbul="İstanbul, Türkiye'de Marmara Bölgesi'nde yer alan şehir ve Türkiye Cumhuriyeti Devletinin 81 ilinden biridir. Ülkenin nüfus bakımından en çok göç alan ve en kalabalık ilidir. Ekonomik, tarihî ve sosyo-kültürel açıdan önde gelen şehirlerden biridir. Şehir, iktisadi büyüklük açısından dünyada 34. sırada yer alır. Nüfuslarına göre şehirler listesinde belediye sınırları göz önüne alınarak yapılan sıralamaya göre Avrupa'da birinci, dünyada ise altıncı sırada yer almaktadır."

soru1 = "İstanbul büyüklük açısından kaçıncı sıradadır?"
print(ask(soru1,istanbul))

soru2 = "İstanbul nerede bulunur?"
print(ask(soru2,istanbul))
```