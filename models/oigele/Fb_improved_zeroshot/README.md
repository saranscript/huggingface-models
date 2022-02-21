---
pipeline_tag: zero-shot-classification
datasets:
- multi_nli
widget:
- text: "natural language processing"
  candidate_labels: "Location & Address, Employment, Organizational, Name, Service, Studies, Science"
  hypothesis_template: "This is {}." 
---

# Fb_improved_zeroshot

Zero-Shot Model designed to classify academic search logs in German and English. Developed by students at ETH Zürich.

This model was trained using the [bart-large-mnli](https://huggingface.co/facebook/bart-large-mnli/) checkpoint provided by Meta on Huggingface. It was then fine-tuned to suit the needs of this project.

## NLI-based Zero-Shot Text Classification

This method is based on Natural Language Inference (NLI), see [Yin et al.](https://arxiv.org/abs/1909.00161).
The following tutorials are taken from the model card of [bart-large-mnli](https://huggingface.co/facebook/bart-large-mnli/).

#### With the zero-shot classification pipeline
The model can be loaded with the `zero-shot-classification` pipeline like so:
```python
from transformers import pipeline
classifier = pipeline("zero-shot-classification",
                      model="oigele/Fb_improved_zeroshot")
```
You can then use this pipeline to classify sequences into any of the class names you specify.
```python
sequence_to_classify = "natural language processing"
candidate_labels = ['Location & Address', 'Employment', 'Organizational', 'Name', 'Service', 'Studies', 'Science']
classifier(sequence_to_classify, candidate_labels)
```
If more than one candidate label can be correct, pass `multi_class=True` to calculate each class independently:
```python
candidate_labels = ['Location & Address', 'Employment', 'Organizational', 'Name', 'Service', 'Studies', 'Science']
classifier(sequence_to_classify, candidate_labels, multi_class=True)
```
#### With manual PyTorch
```python
# pose sequence as a NLI premise and label as a hypothesis
from transformers import AutoModelForSequenceClassification, AutoTokenizer
nli_model = AutoModelForSequenceClassification.from_pretrained('oigele/Fb_improved_zeroshot/')
tokenizer = AutoTokenizer.from_pretrained('facebook/bart-large-mnli')
premise = sequence
hypothesis = f'This is {label}.'
# run through model pre-trained on MNLI
x = tokenizer.encode(premise, hypothesis, return_tensors='pt',
                     truncation_strategy='only_first')
logits = nli_model(x.to(device))[0]
# we throw away "neutral" (dim 1) and take the probability of
# "entailment" (2) as the probability of the label being true 
entail_contradiction_logits = logits[:,[0,2]]
probs = entail_contradiction_logits.softmax(dim=1)
prob_label_is_true = probs[:,1]
