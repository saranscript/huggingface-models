---
language: "ca"
license: mit
tags:
- summarization
widget:
- text: "El projecte AINA generarà els recursos digitals i lingüístics necessaris per facilitar el desenvolupament d’aplicacions basades en la intel·ligència artificial i les tecnologies de la llengua, com ara els assistents de veu, els traductors automàtics o els agents conversacionals en català. L’objectiu últim és que la ciutadania pugui participar en català en el món digital al mateix nivell que els parlants d’una llengua global, com ara l’anglès, i evitar així l’extinció digital de la llengua. El primer recurs generat és el corpus del català per entrenar els algoritmes d’intel·ligència artificial (IA), el més gran creat fins al moment, amb 1.770 milions de metadades associades a paraules. El proper pas serà generar els models de la llengua, models de la parla i models de traducció utilitzant xarxes neuronals multicapa, perquè les empreses que creen aplicacions basades en intel·ligència artificial (IA), com ara assistents de veu, traductors automàtics, agents conversacionals, etc., puguin fer-ho fàcilment en català."
---
## BART-Ca fine-tuned on the CaSum dataset for summarization

## Model description

The [BART-ca](https://huggingface.co/projecte-aina/bart-base-ca) model has been fine-tuned on summarization with the [CaSum](https://huggingface.co/datasets/projecte-aina/casum) dataset that has been created along with the model. We also evaluate on an out-of-distribution dataset, [VilaSum](https://huggingface.co/datasets/projecte-aina/vilasum).

### How to use

Here is how to use this model with the [pipeline API](https://huggingface.co/transformers/main_classes/pipelines.html):

```python
from transformers import pipeline
summarizer = pipeline("summarization", model="projecte-aina/bart-base-ca-casum")
ARTICLE = """"El projecte AINA generarà els recursos digitals i lingüístics necessaris per facilitar el desenvolupament d’aplicacions basades en la intel·ligència artificial i les tecnologies de la llengua, com ara els assistents de veu, els traductors automàtics o els agents conversacionals en català. L’objectiu últim és que la ciutadania pugui participar en català en el món digital al mateix nivell que els parlants d’una llengua global, com ara l’anglès, i evitar així l’extinció digital de la llengua. El primer recurs generat és el corpus del català per entrenar els algoritmes d’intel·ligència artificial (IA), el més gran creat fins al moment, amb 1.770 milions de metadades associades a paraules. El proper pas serà generar els models de la llengua, models de la parla i models de traducció utilitzant xarxes neuronals multicapa, perquè les empreses que creen aplicacions basades en intel·ligència artificial (IA), com ara assistents de veu, traductors automàtics, agents conversacionals, etc., puguin fer-ho fàcilment en català."""
print(summarizer(ARTICLE, max_length=130, min_length=30, do_sample=False))
>>> [{'summary_text': 'El projecte AINA generarà els recursos digitals i lingüístics necessaris per al desenvolupament d’aplicacions basades en la intel·ligència artificial en català’'}]
```

## Evaluation

Below the evaluation results on the summarization task compared with the multilingual mBERT and the Catalan [NASCA](https://huggingface.co/ELiRF/NASCA) with two different testsets: [CaSum](https://huggingface.co/datasets/projecte-aina/casum) and [VilaSum](https://huggingface.co/datasets/projecte-aina/vilasum).

|Test set  | Model  | Rouge-1  |  Rouge-L  |
| ------------|:-------------:| -----:|:------|
|CaSum | BART-Ca  |  41.39  |  36.14  |
| | NASCA  |  24.42  |  19.89  |
| | mBART  |  **43.95**  |  **38.11**  |
|VilaSum  | BART-Ca  |  **35.04**  |  **29.70**  |
| | NASCA  |  23.18 |  19.09 |
| | mBART  |  33.17  |  27.52  |

## BibTeX  citation

If you use any of these resources (datasets or models) in your work, please cite our latest preprint:

```bibtex
@misc{degibert2022sequencetosequence,
      title={Sequence-to-Sequence Resources for Catalan}, 
      author={Ona de Gibert and Ksenia Kharitonova and Blanca Calvo Figueras and Jordi Armengol-Estapé and Maite Melero},
      year={2022},
      eprint={2202.06871},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

## Funding
This work was funded by the [MT4All CEF](https://ec.europa.eu/inea/en/connecting-europe-facility/cef-telecom/2019-eu-ia-0031) project.