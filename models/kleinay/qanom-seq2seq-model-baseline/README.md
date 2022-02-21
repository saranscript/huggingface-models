---
language:
- en
tags:
- semantic-role-labeling
- question-answer generation
- pytorch
datasets:
- kleinay/qanom
---

# A Seq2Seq model for QANom parsing

This is a `t5-small` pretrained model, fine-tuned on the task of generating QANom QAs. 

"QANom" stands for "QASRL for Nominalizations", which is an adaptation of [QASRL (Question-Answer driven Semantic Role Labeling)](https://qasrl.org) for the nominal predicates domain. See the [QANom paper](https://aclanthology.org/2020.coling-main.274/) for details about the task. The QANom Dataset official site is a [Google drive](https://drive.google.com/drive/folders/15PHKVdPm65ysgdkV47z6J_73kETk7_of), but we also wrapped it into a [Huggingface Dataset](https://huggingface.co/datasets/biu-nlp/qanom), which is easier to plug-and-play with (check out our [HF profile](https://huggingface.co/biu-nlp) for other related datasets, such as QASRL, QAMR, QADiscourse, and QA-Align). 

## Demo

Visit [our demo](https://huggingface.co/spaces/kleinay/qanom-seq2seq-demo) for interactively exploring our model!
      
## Usage 

The model and tokenizer can be downloaded as simply as running:
```python
import transformers
model = transformers.AutoModelForSeq2SeqLM.from_pretrained("kleinay/qanom-seq2seq-model-baseline")
tokenizer = transformers.AutoTokenizer.from_pretrained("kleinay/qanom-seq2seq-model-baseline")
```

However, the model fine-tuning procedure involves input preprocessing (marking the predicate in the sentence, T5's "task prefix", incorporating the predicate type and/or the verbal for of the nominalization) and output postprocessing (parsing the sequence into a list of QASRL-formatted QAs).  
In order to use the model for QANom parsing easily, we suggest downloading the [`pipeline.py`](https://huggingface.co/kleinay/qanom-seq2seq-model-baseline/blob/main/pipeline.py) file from this repository, and then use the `QASRL_Pipeline` class:

```python
from pipeline import QASRL_Pipeline
pipe = QASRL_Pipeline("kleinay/qanom-seq2seq-model-baseline")
pipe("The student was interested in Luke 's <predicate> research about see animals .", verb_form="research", predicate_type="nominal")
``` 
Which will output:
```json
[{'generated_text': 'who _ _ researched something _ _ ?<extra_id_7> Luke', 
  'QAs': [{'question': 'who researched something ?', 'answers': ['Luke']}]}]
```   
You can learn more about using `transformers.pipelines` in the [official docs](https://huggingface.co/docs/transformers/main_classes/pipelines).

Notice that you need to specify which word in the sentence is the predicate, about which the question will interrogate. By default, you should precede the predicate with the `<predicate>` symbol, but you can also specify your own predicate marker:
```python
pipe("The student was interested in Luke 's <PRED> research about see animals .", verb_form="research", predicate_type="nominal", predicate_marker="<PRED>")
```
In addition, you can specify additional kwargs for controling the model's decoding algorithm:
```python
pipe("The student was interested in Luke 's <predicate> research about see animals .", verb_form="research", predicate_type="nominal", num_beams=3)
```


            