---
language: 
- english
thumbnail: 
tags:
- token classification
license: 
datasets:
- EMBO/sd-nlp
metrics:
-
---

# sd-ner

## Model description

This model is a [RoBERTa base model](https://huggingface.co/roberta-base) that was further trained using a masked language modeling task on a compendium of english scientific textual examples from the life sciences using the [BioLang dataset](https://huggingface.co/datasets/EMBO/biolang). It was then fine-tuned for token classification on the SourceData [sd-nlp](https://huggingface.co/datasets/EMBO/sd-nlp) dataset wit the `NER` task to perform Named Entity Recognition of bioentities. 


## Intended uses & limitations

#### How to use

The intended use of this model is for Named Entity Recognition of biological entitie used in SourceData annotations (https://sourcedata.embo.org), including small molecules, gene products (genes and proteins), subcellular components, cell line and cell types, organ and tissues, species as well as experimental methods.

To have a quick check of the model:

```python
from transformers import pipeline, RobertaTokenizerFast, RobertaForTokenClassification
example = """<s> F. Western blot of input and eluates of Upf1 domains purification in a Nmd4-HA strain. The band with the # might corresponds to a dimer of Upf1-CH, bands marked with a star correspond to residual signal with the anti-HA antibodies (Nmd4). Fragments in the eluate have a smaller size because the protein A part of the tag was removed by digestion with the TEV protease. G6PDH served as a loading control in the input samples </s>"""
tokenizer = RobertaTokenizerFast.from_pretrained('roberta-base', max_len=512)
model = RobertaForTokenClassification.from_pretrained('EMBO/sd-ner')
ner = pipeline('ner', model, tokenizer=tokenizer)
res = ner(example)
for r in res:
    print(r['word'], r['entity'])
```

#### Limitations and bias

The model must be used with the `roberta-base` tokenizer.

## Training data

The model was trained for token classification using the [EMBO/sd-nlp `NER`](https://huggingface.co/datasets/EMBO/sd-nlp) dataset wich includes manually annotated examples.

## Training procedure

The training was run on a NVIDIA DGX Station with 4XTesla V100 GPUs.

Training code is available at https://github.com/source-data/soda-roberta

- Command: `python -m tokcl.train NER  --num_train_epochs=3.5`
- Tokenizer vocab size: 50265
- Training data: EMBO/sd-nlp NER
- Training with 31410 examples.
- Evaluating on 8861 examples.
- Training on 15 features: O, I-SMALL_MOLECULE, B-SMALL_MOLECULE, I-GENEPROD, B-GENEPROD, I-SUBCELLULAR, B-SUBCELLULAR, I-CELL, B-CELL, I-TISSUE, B-TISSUE, I-ORGANISM, B-ORGANISM, I-EXP_ASSAY, B-EXP_ASSAY
- Epochs: 3.5
- `per_device_train_batch_size`: 32
- `per_device_eval_batch_size`: 32
- `learning_rate`: 0.0001
- `weight_decay`: 0.0
- `adam_beta1`: 0.9
- `adam_beta2`: 0.999
- `adam_epsilon`: 1e-08
- `max_grad_norm`: 1.0

## Eval results

On test set with `sklearn.metrics`:

```
                precision    recall  f1-score   support

          CELL       0.77      0.81      0.79      3477
     EXP_ASSAY       0.71      0.70      0.71      7049
      GENEPROD       0.86      0.90      0.88     16140
      ORGANISM       0.80      0.82      0.81      2759
SMALL_MOLECULE       0.78      0.82      0.80      4446
   SUBCELLULAR       0.71      0.75      0.73      2125
        TISSUE       0.70      0.75      0.73      1971

     micro avg       0.79      0.82      0.81     37967
     macro avg       0.76      0.79      0.78     37967
  weighted avg       0.79      0.82      0.81     37967
```
