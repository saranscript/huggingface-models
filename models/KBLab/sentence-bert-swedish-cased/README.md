---
pipeline_tag: sentence-similarity
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
widget:
- source_sentence: "Mannen åt mat."
  sentences:
    - "Han förtärde en närande och nyttig måltid."
    - "Det var ett sunkigt hak med ganska gott käk."
    - "Han inmundigade middagen tillsammans med ett glas rödvin."
    - "Potatischips är jättegoda."
    - "Tryck på knappen för att få tala med kundsupporten."
  example_title: "Mat"
- source_sentence: "Kan jag deklarera digitalt från utlandet?"
  sentences:
    - "Du som befinner dig i utlandet kan deklarera digitalt på flera olika sätt."
    - "Du som har kvarskatt att betala ska göra en inbetalning till ditt skattekonto."
    - "Efter att du har deklarerat går vi igenom uppgifterna i din deklaration och räknar ut din skatt."
    - "I din deklaration som du får från oss har vi räknat ut vad du ska betala eller få tillbaka."
    - "Tryck på knappen för att få tala med kundsupporten."
  example_title: "Skatteverket FAQ"
- source_sentence: "Hon kunde göra bakåtvolter."
  sentences:
    - "Hon var atletisk."
    - "Hon var bra på gymnastik."
    - "Hon var inte atletisk."
    - "Hon var oförmögen att flippa baklänges."
  example_title: "Gymnastik"
---

# KBLab/sentence-bert-swedish-cased

This is a [sentence-transformers](https://www.SBERT.net) model: It maps Swedish sentences & paragraphs to a 768 dimensional dense vector space and can be used for tasks like clustering or semantic search. This model is a bilingual Swedish-English model trained according to instructions in the paper [Making Monolingual Sentence Embeddings Multilingual using Knowledge Distillation](https://arxiv.org/pdf/2004.09813.pdf) and the [documentation](https://www.sbert.net/examples/training/multilingual/README.html) accompanying its companion python package. We have used the strongest available pretrained English Bi-Encoder ([paraphrase-mpnet-base-v2](https://www.sbert.net/docs/pretrained_models.html#sentence-embedding-models)) as a teacher model, and the pretrained Swedish [KB-BERT](https://huggingface.co/KB/bert-base-swedish-cased) as the student model. 

A more detailed description of the model can be found in an article we published on the [KBLab blog](https://kb-labb.github.io/posts/2021-08-23-a-swedish-sentence-transformer/). 

<!--- Describe your model here -->

## Usage (Sentence-Transformers)

Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:

```
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer
sentences = ["Det här är en exempelmening", "Varje exempel blir konverterad"]

model = SentenceTransformer('KBLab/sentence-bert-swedish-cased')
embeddings = model.encode(sentences)
print(embeddings)
```



## Usage (HuggingFace Transformers)
Without [sentence-transformers](https://www.SBERT.net), you can use the model like this: First, you pass your input through the transformer model, then you have to apply the right pooling-operation on-top of the contextualized word embeddings.

```python
from transformers import AutoTokenizer, AutoModel
import torch


#Mean Pooling - Take attention mask into account for correct averaging
def mean_pooling(model_output, attention_mask):
    token_embeddings = model_output[0] #First element of model_output contains all token embeddings
    input_mask_expanded = attention_mask.unsqueeze(-1).expand(token_embeddings.size()).float()
    return torch.sum(token_embeddings * input_mask_expanded, 1) / torch.clamp(input_mask_expanded.sum(1), min=1e-9)


# Sentences we want sentence embeddings for
sentences = ['Det här är en exempelmening', 'Varje exempel blir konverterad']

# Load model from HuggingFace Hub
tokenizer = AutoTokenizer.from_pretrained('KBLab/sentence-bert-swedish-cased')
model = AutoModel.from_pretrained('KBLab/sentence-bert-swedish-cased')

# Tokenize sentences
encoded_input = tokenizer(sentences, padding=True, truncation=True, return_tensors='pt')

# Compute token embeddings
with torch.no_grad():
    model_output = model(**encoded_input)

# Perform pooling. In this case, max pooling.
sentence_embeddings = mean_pooling(model_output, encoded_input['attention_mask'])

print("Sentence embeddings:")
print(sentence_embeddings)
```



## Evaluation Results

<!--- Describe how your model was evaluated -->

The model was primarily evaluated on [SweParaphrase v1.0](https://spraakbanken.gu.se/en/resources/sweparaphrase). This test set is part of [SuperLim](https://spraakbanken.gu.se/en/resources/superlim) -- a Swedish evaluation suite for natural langage understanding tasks.  We calculated Pearson and Spearman correlation between predicted model similarity scores and the human similarity score labels. The model achieved a Pearson correlation coefficient of **0.918** and a Spearman's rank correlation coefficient of **0.911**.

The following code snippet can be used to reproduce the above results:

```python
from sentence_transformers import SentenceTransformer
import pandas as pd

df = pd.read_csv(
    "sweparaphrase-dev-165.csv",
    sep="\t",
    header=None,
    names=[
        "original_id",
        "source",
        "type",
        "sentence_swe1",
        "sentence_swe2",
        "score",
        "sentence1",
        "sentence2",
    ],
)

model = SentenceTransformer("KBLab/sentence-bert-swedish-cased")

sentences1 = df["sentence_swe1"].tolist()
sentences2 = df["sentence_swe2"].tolist()

# Compute embedding for both lists
embeddings1 = model.encode(sentences1, convert_to_tensor=True)
embeddings2 = model.encode(sentences2, convert_to_tensor=True)

# Compute cosine similarity after normalizing
embeddings1 /= embeddings1.norm(dim=-1, keepdim=True)
embeddings2 /= embeddings2.norm(dim=-1, keepdim=True)

cosine_scores = embeddings1 @ embeddings2.t()
sentence_pair_scores = cosine_scores.diag()

df["model_score"] = sentence_pair_scores.cpu().tolist()
print(df[["score", "model_score"]].corr(method="spearman"))
print(df[["score", "model_score"]].corr(method="pearson"))
```

Examples how to evaluate the model on other test sets of the SuperLim suites can be found on the following links: [evaluate_faq.py](https://github.com/kb-labb/swedish-sbert/blob/main/evaluate_faq.py) (Swedish FAQ), [evaluate_swesat.py](https://github.com/kb-labb/swedish-sbert/blob/main/evaluate_swesat.py) (SweSAT synonyms), [evaluate_supersim.py](https://github.com/kb-labb/swedish-sbert/blob/main/evaluate_supersim.py) (SuperSim).

## Training

An article with more details on data and the model can be found on the [KBLab blog](https://kb-labb.github.io/posts/2021-08-23-a-swedish-sentence-transformer/). 

Around 14.6 million sentences from English-Swedish parallel corpuses were used to train the model. Data was sourced from the [Open Parallel Corpus](https://opus.nlpl.eu/) (OPUS) and downloaded via the python package [opustools](https://pypi.org/project/opustools/). Datasets used were: JW300, Europarl, EUbookshop, EMEA, TED2020, Tatoeba and OpenSubtitles. 

The model was trained with the parameters:

**DataLoader**:

`torch.utils.data.dataloader.DataLoader` of length 227832 with parameters:
```
{'batch_size': 64, 'sampler': 'torch.utils.data.sampler.RandomSampler', 'batch_sampler': 'torch.utils.data.sampler.BatchSampler'}
```

**Loss**:

`sentence_transformers.losses.MSELoss.MSELoss` 

Parameters of the fit()-Method:
```
{
    "callback": null,
    "epochs": 7,
    "evaluation_steps": 1000,
    "evaluator": "sentence_transformers.evaluation.SequentialEvaluator.SequentialEvaluator",
    "max_grad_norm": 1,
    "optimizer_class": "<class 'transformers.optimization.AdamW'>",
    "optimizer_params": {
        "correct_bias": false,
        "eps": 1e-06,
        "lr": 2e-05
    },
    "scheduler": "WarmupLinear",
    "steps_per_epoch": null,
    "warmup_steps": 10000,
    "weight_decay": 0.01
}
```


## Full Model Architecture
```
SentenceTransformer(
  (0): Transformer({'max_seq_length': 256, 'do_lower_case': False}) with Transformer model: BertModel 
  (1): Pooling({'word_embedding_dimension': 768, 'pooling_mode_cls_token': False, 'pooling_mode_mean_tokens': True, 'pooling_mode_max_tokens': False, 'pooling_mode_mean_sqrt_len_tokens': False})
)
```

## Citing & Authors

<!--- Describe where people can find more information -->
This model was trained by KBLab, a data lab at the National Library of Sweden. 

You can cite the article on our blog: https://kb-labb.github.io/posts/2021-08-23-a-swedish-sentence-transformer/ .

## Acknowledgements

We gratefully acknowledge the HPC RIVR consortium (www.hpc-rivr.si) and EuroHPC JU ([eurohpc-ju.europa.eu](eurohpc-ju.europa.eu)) for funding this research by providing computing resources of the HPC system Vega at the Institute of Information Science (www.izum.si).