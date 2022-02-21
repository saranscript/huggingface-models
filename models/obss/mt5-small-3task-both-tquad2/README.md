---
language: tr
datasets:
- tquad1
- tquad2
- xquad 
tags: 
- text2text-generation
- question-generation
- answer-extraction
- question-answering
- text-generation
pipeline_tag: text2text-generation
widget:
- text: "answer: film ve TV haklarını context: Legendary Entertainment, 2016 yılında bilimkurgu romanı Dune'un <hl> film ve TV haklarını <hl> satın aldı. Geliştirme kısa bir süre sonra başladı. Villeneuve projeye olan ilgisini dile getirdi ve resmi olarak yönetmen olarak imza attı. Roth ve Spaihts ile birlikte çalışarak senaryoyu iki bölüme ayırdı ve 1965 romanının 21. yüzyıla güncellenmiş bir uyarlamasını ekledi."
  example_title: "Question Generation (Movie)"
- text: "answer: bir antlaşma yaparak context: Fatih Sultan Mehmet, Cenevizlilerin önemli üslerinden Amasra’yı aldı. 1479’da <hl> bir antlaşma yaparak <hl> Venedik'le  16 yıllık savaşa son verdi."
  example_title: "Question Generation (History)"
- text: "answer: Venedik'le context: Cenevizlilerin önemli üslerinden Amasra’yı aldı. 1479’da bir antlaşma yaparak <hl> Venedik'le <hl> 16 yıllık savaşa sona verdi."
  example_title: "Question Generation (History 2)"
- text: "extract answers: Cenevizlilerin önemli üslerinden Amasra’yı aldı. <hl> 1479’da bir antlaşma yaparak Venedik'le 16 yıllık savaşa sona verdi. <hl>"
  example_title: "Answer Extraction (History)"
- text: "question: Bu model ne ise yarar? context: Çalışmada sunulan yöntemle, Türkçe metinlerden otomatik olarak soru ve cevap üretilebilir. Bu proje ile paylaşılan kaynak kodu ile Türkçe Soru Üretme / Soru Cevaplama konularında yeni akademik çalışmalar yapılabilir. Projenin detaylarına paylaşılan Github ve Arxiv linklerinden ulaşılabilir."
  example_title: "Answer Extraction (Open Domain)"
license: cc-by-4.0
---

# mt5-small for Turkish Question Generation
Automated question generation and question answering using text-to-text transformers by OBSS AI.
```python
from core.api import GenerationAPI
generation_api = GenerationAPI('mt5-small-3task-both-tquad2', qg_format='both')
```

##  Citation 📜
```
@article{akyon2021automated,
  title={Automated question generation and question answering from Turkish texts using text-to-text transformers},
  author={Akyon, Fatih Cagatay and Cavusoglu, Devrim and Cengiz, Cemil and Altinuc, Sinan Onur and Temizel, Alptekin},
  journal={arXiv preprint arXiv:2111.06476},
  year={2021}
}
```

## Overview ✔️
**Language model:** mt5-small  
**Language:** Turkish  
**Downstream-task:** Extractive QA/QG, Answer Extraction  
**Training data:** TQuADv2-train
**Code:**  https://github.com/obss/turkish-question-generation  
**Paper:**  https://arxiv.org/abs/2111.06476  

## Hyperparameters
```
batch_size = 256
n_epochs = 15
base_LM_model = "mt5-small"
max_source_length = 512
max_target_length = 64
learning_rate = 1.0e-3
task_lisst = ["qa", "qg", "ans_ext"]
qg_format = "both"
``` 

## Performance
Refer to [paper](https://arxiv.org/abs/2111.06476).

## Usage 🔥
```python
from core.api import GenerationAPI

generation_api = GenerationAPI('mt5-small-3task-both-tquad2', qg_format='both')

context = """
Bu modelin eğitiminde, Türkçe soru cevap verileri kullanılmıştır.
Çalışmada sunulan yöntemle, Türkçe metinlerden otomatik olarak soru ve cevap
üretilebilir. Bu proje ile paylaşılan kaynak kodu ile Türkçe Soru Üretme
/ Soru Cevaplama konularında yeni akademik çalışmalar yapılabilir.
Projenin detaylarına paylaşılan Github ve Arxiv linklerinden ulaşılabilir.
"""

# a) Fully Automated Question Generation
generation_api(task='question-generation', context=context)

# b) Question Answering
question = "Bu model ne işe yarar?"
generation_api(task='question-answering', context=context, question=question)

# b) Answer Extraction
generation_api(task='answer-extraction', context=context)
```
