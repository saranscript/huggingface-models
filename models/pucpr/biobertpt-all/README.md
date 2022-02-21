---
language: "pt"
widget:
- text: "O paciente recebeu [MASK] do hospital."
- text: "O médico receitou a medicação para controlar a [MASK]."
- text: "O principal [MASK] da COVID-19 é tosse seca."
- text: "O vírus da gripe apresenta um [MASK] constituído por segmentos de ácido ribonucleico."

datasets: 
- biomedical literature from Scielo and Pubmed
thumbnail: "https://raw.githubusercontent.com/HAILab-PUCPR/BioBERTpt/master/images/logo-biobertpr1.png"
---

<img src="https://raw.githubusercontent.com/HAILab-PUCPR/BioBERTpt/master/images/logo-biobertpr1.png" alt="Logo BioBERTpt">

# BioBERTpt - Portuguese Clinical and Biomedical BERT

The [BioBERTpt - A Portuguese Neural Language Model for Clinical Named Entity Recognition](https://www.aclweb.org/anthology/2020.clinicalnlp-1.7/) paper contains clinical and biomedical BERT-based models for Portuguese Language, initialized with BERT-Multilingual-Cased & trained on clinical notes and biomedical literature. 

This model card describes the BioBERTpt(all) model, a full version with clinical narratives and biomedical literature in Portuguese language. 

## How to use the model

Load the model via the transformers library:
```
from transformers import AutoTokenizer, AutoModel
tokenizer = AutoTokenizer.from_pretrained("pucpr/biobertpt-all")
model = AutoModel.from_pretrained("pucpr/biobertpt-all")
```

## More Information

Refer to the original paper, [BioBERTpt - A Portuguese Neural Language Model for Clinical Named Entity Recognition](https://www.aclweb.org/anthology/2020.clinicalnlp-1.7/) for additional details and performance on Portuguese NER tasks.

## Acknowledgements

This study was financed in part by the Coordenação de Aperfeiçoamento de Pessoal de Nível Superior - Brasil (CAPES) - Finance Code 001.

## Citation

```
@inproceedings{schneider-etal-2020-biobertpt,
    title = "{B}io{BERT}pt - A {P}ortuguese Neural Language Model for Clinical Named Entity Recognition",
    author = "Schneider, Elisa Terumi Rubel  and
      de Souza, Jo{\~a}o Vitor Andrioli  and
      Knafou, Julien  and
      Oliveira, Lucas Emanuel Silva e  and
      Copara, Jenny  and
      Gumiel, Yohan Bonescki  and
      Oliveira, Lucas Ferro Antunes de  and
      Paraiso, Emerson Cabrera  and
      Teodoro, Douglas  and
      Barra, Cl{\'a}udia Maria Cabral Moro",
    booktitle = "Proceedings of the 3rd Clinical Natural Language Processing Workshop",
    month = nov,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.clinicalnlp-1.7",
    pages = "65--72",
    abstract = "With the growing number of electronic health record data, clinical NLP tasks have become increasingly relevant to unlock valuable information from unstructured clinical text. Although the performance of downstream NLP tasks, such as named-entity recognition (NER), in English corpus has recently improved by contextualised language models, less research is available for clinical texts in low resource languages. Our goal is to assess a deep contextual embedding model for Portuguese, so called BioBERTpt, to support clinical and biomedical NER. We transfer learned information encoded in a multilingual-BERT model to a corpora of clinical narratives and biomedical-scientific papers in Brazilian Portuguese. To evaluate the performance of BioBERTpt, we ran NER experiments on two annotated corpora containing clinical narratives and compared the results with existing BERT models. Our in-domain model outperformed the baseline model in F1-score by 2.72{\%}, achieving higher performance in 11 out of 13 assessed entities. We demonstrate that enriching contextual embedding models with domain literature can play an important role in improving performance for specific NLP tasks. The transfer learning process enhanced the Portuguese biomedical NER model by reducing the necessity of labeled data and the demand for retraining a whole new model.",
}
```

## Questions?

Post a Github issue on the [BioBERTpt repo](https://github.com/HAILab-PUCPR/BioBERTpt).