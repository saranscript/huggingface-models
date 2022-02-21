# Multi-lingual Question Generating Model (mt5-base)
Give the model a passage and it will generate a question about the passage.  

## Trained on the following datasets:

- [SQuAD (English)](https://rajpurkar.github.io/SQuAD-explorer/)
- [TyDiQA-GoldP (Arabic, Bengali, Finnish, Japanese, Indonesian, Kiswahili, Korean, Russian, Telugu, Thai)](https://github.com/google-research-datasets/tydiqa)
- [MLQA (Arabic, Chinese, English, German, Hindi, Spanish, Vietnames)](https://github.com/facebookresearch/MLQA)
- [XQuAD (Arabic, Chinese, German, Greek, Hindi, Russian, Spanish, Thai, Turkish Vietnamese)](https://github.com/deepmind/xquad)
- [GermanQuAD (German)](https://huggingface.co/datasets/deepset/germanquad)
- [Persian QA (Persian)](https://www.kaggle.com/sajjadayobi360/persianqa)
- [Bengali QA (Bengali)](https://www.kaggle.com/mayeesha/bengali-question-answering-dataset)
- [chaii (Hindi, Tamil)](https://www.kaggle.com/c/chaii-hindi-and-tamil-question-answering/data)


## Training details
I used [flax summarization script](https://github.com/huggingface/transformers/tree/master/examples/flax/summarization) and a TPU v3-8. Summarization expects a text column and a summary column. For question generation training, use the context column instead of text column and question instead of summary column.


There is no guarantee that it will produce a question in the language of the passage, but it usually does. Lower resource languages will likely have lower quality questions.


## Using the model

#### PyTorch version
```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
  
tokenizer = AutoTokenizer.from_pretrained("nbroad/mt5-base-qgen")
model = AutoModelForSeq2SeqLM.from_pretrained("nbroad/mt5-base-qgen", from_flax=True)

text = "Hugging Face has seen rapid growth in its \
popularity since the get-go. It is definitely doing\
 the right things to attract more and more people to \
 its platform, some of which are on the following lines:\
Community driven approach through large open source repositories \
along with paid services. Helps to build a network of like-minded\
 people passionate about open source. \
Attractive price point. The subscription-based features, e.g.: \
Inference based API, starts at a price of $9/month.\
"

inputs = tokenizer(text, return_tensors="pt")
output = model.generate(**inputs, max_length=40)

tokenizer.decode(output[0], skip_special_tokens=True)
# What is Hugging Face's price point?
```

#### Flax version
```python
from transformers import AutoTokenizer, FlaxAutoModelForSeq2SeqLM
  
tokenizer = AutoTokenizer.from_pretrained("nbroad/mt5-base-qgen")
model = FlaxAutoModelForSeq2SeqLM.from_pretrained("nbroad/mt5-base-qgen")

text = "A un año y tres días de que el balón ruede \
en el Al Bayt Stadium inaugurando el Mundial 2022, \
ya se han dibujado los primeros bocetos de la próxima \
Copa del Mundo.13 selecciones están colocadas en el \
mapa con la etiqueta de clasificadas y tienen asegurado\
 pisar los verdes de Qatar en la primera fase final \
 otoñal. Serbia, Dinamarca, España, Países Bajos, \
 Suiza, Croacia, Francia, Inglaterra, Bélgica, Alemania,\
  Brasil, Argentina y Qatar, como anfitriona, entrarán en \
  el sorteo del 1 de abril de 2022 en Doha en el que 32 \
  países serán repartidos en sus respectivos grupos. \
"

inputs = tokenizer(text, return_tensors="pt")
output = model.generate(**inputs, max_length=40)

tokenizer.decode(output["sequences"][0], skip_special_tokens=True)
# ¿Cuántos países entrarán en el sorteo del Mundial 2022?
```


Model trained on Cloud TPUs from Google's TPU Research Cloud (TRC)