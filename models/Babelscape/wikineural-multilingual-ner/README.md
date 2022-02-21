---
annotations_creators:
- machine-generated
language_creators:
- machine-generated
widget:
- text: "My name is Wolfgang and I live in Berlin."
- text: "Mi nombre es Sarah y vivo en Londres."
- text: "Меня зовут Симона, и я живу в Риме."
tags:
- named-entity-recognition
datasets:
- Babelscape/wikineural
language:
- de
- en
- es
- fr
- it
- nl
- pl
- pt
- ru
license:
- cc-by-nc-sa-4.0
pretty_name: wikineural-dataset
source_datasets:
- original
task_categories:
- structure-prediction
task_ids:
- named-entity-recognition

---

## Model Description

- **Summary:** mBERT model fine-tuned for 3 epochs on the recently-introduced WikiNEuRal dataset for Multilingual NER. The system supports the 9 languages covered by WikiNEuRal (de, en, es, fr, it, nl, pl, pt, ru), and it was trained on all 9 languages jointly. For a stronger baseline system (mBERT + Bi-LSTM + CRF) look at the official repository.
- **Official Repository:** [https://github.com/Babelscape/wikineural](https://github.com/Babelscape/wikineural)
- **Paper:** [https://aclanthology.org/wikineural](https://aclanthology.org/2021.findings-emnlp.215/)

#### How to use

You can use this model with Transformers *pipeline* for NER.

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline

tokenizer = AutoTokenizer.from_pretrained("Babelscape/wikineural-multilingual-ner")
model = AutoModelForTokenClassification.from_pretrained("Babelscape/wikineural-multilingual-ner")

nlp = pipeline("ner", model=model, tokenizer=tokenizer)
example = "My name is Wolfgang and I live in Berlin"

ner_results = nlp(example)
print(ner_results)
```

#### Limitations and bias

This model is trained on WikiNEuRal, a state-of-the-art dataset for Multilingual NER automatically derived from Wikipedia. Therefore, it may not generalize well on all textual genres (e.g. news). On the other hand, models trained only on news articles (e.g. only on CoNLL03) have been proven to obtain much lower scores on encyclopedic articles. To obtain a more robust system, we encourage to train a system on the combination of WikiNEuRal + CoNLL.

## Licensing Information

Contents of this repository are restricted to only non-commercial research purposes under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/). Copyright of the dataset contents and models belongs to the original copyright holders.

## Citation Information

```bibtex
@inproceedings{tedeschi-etal-2021-wikineural-combined,
    title = "{W}iki{NE}u{R}al: {C}ombined Neural and Knowledge-based Silver Data Creation for Multilingual {NER}",
    author = "Tedeschi, Simone  and
      Maiorca, Valentino  and
      Campolungo, Niccol{\`o}  and
      Cecconi, Francesco  and
      Navigli, Roberto",
    booktitle = "Findings of the Association for Computational Linguistics: EMNLP 2021",
    month = nov,
    year = "2021",
    address = "Punta Cana, Dominican Republic",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.findings-emnlp.215",
    pages = "2521--2533",
    abstract = "Multilingual Named Entity Recognition (NER) is a key intermediate task which is needed in many areas of NLP. In this paper, we address the well-known issue of data scarcity in NER, especially relevant when moving to a multilingual scenario, and go beyond current approaches to the creation of multilingual silver data for the task. We exploit the texts of Wikipedia and introduce a new methodology based on the effective combination of knowledge-based approaches and neural models, together with a novel domain adaptation technique, to produce high-quality training corpora for NER. We evaluate our datasets extensively on standard benchmarks for NER, yielding substantial improvements up to 6 span-based F1-score points over previous state-of-the-art systems for data creation.",
}
```

