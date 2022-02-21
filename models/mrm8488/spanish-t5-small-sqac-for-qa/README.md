---
language: es
tags:
- QA
- Q&A
datasets:
- BSC-TeMU/SQAC
widget:
- text: "question: ¿Cuál es el nombre que se le da a la unidad morfológica y funcional de los seres vivos? context: La célula (del latín cellula, diminutivo de cella, ‘celda’) es la unidad morfológica y funcional de todo ser vivo. De hecho, la célula es el elemento de menor tamaño que puede considerarse vivo.\u200b De este modo, puede clasificarse a los organismos vivos según el número de células que posean: si solo tienen una, se les denomina unicelulares (como pueden ser los protozoos o las bacterias, organismos microscópicos); si poseen más, se les llama pluricelulares. En estos últimos el número de células es variable: de unos pocos cientos, como en algunos nematodos, a cientos de billones (1014), como en el caso del ser humano. Las células suelen poseer un tamaño de 10 µm y una masa de 1 ng, si bien existen células mucho mayores."
---

# Spanish T5 (small) fine-tuned on **SQAC** for  Spanish **QA** 📖❓
[spanish-T5-small](https://huggingface.co/flax-community/spanish-t5-small) fine-tuned on [SQAC](https://huggingface.co/datasets/BSC-TeMU/SQAC) for **Q&A** downstream task.

## Details of Spanish T5 (small)

T5 (small) like arch trained from scatch on [large_spanish_corpus](https://huggingface.co/datasets/large_spanish_corpus) for **HuggingFace/Flax/Jax Week**.




## Details of the dataset 📚 

This dataset contains 6,247 contexts and 18,817 questions with their answers, 1 to 5 for each fragment.
The sources of the contexts are:
* Encyclopedic articles from [Wikipedia in Spanish](https://es.wikipedia.org/), used under [CC-by-sa licence](https://creativecommons.org/licenses/by-sa/3.0/legalcode). 
* News from [Wikinews in Spanish](https://es.wikinews.org/), used under [CC-by licence](https://creativecommons.org/licenses/by/2.5/). 
* Text from the Spanish corpus [AnCora](http://clic.ub.edu/corpus/en), which is a mix from diferent newswire and literature sources, used under [CC-by licence](https://creativecommons.org/licenses/by/4.0/legalcode). 
This dataset can be used to build extractive-QA.



## Results on test dataset 📝

| Metric | # Value   |
| ------ | --------- |
| **BLEU** | **41.94** |



## Model in Action 🚀

```python
from transformers import T5ForConditionalGeneration, AutoTokenizer
import torch
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
ckpt = 'mrm8488/spanish-t5-small-sqac-for-qa'
tokenizer = AutoTokenizer.from_pretrained(ckpt)
model = T5ForConditionalGeneration.from_pretrained(ckpt).to(device)



def get_answer(question, context):
  input_text = 'question: %s  context: %s' % (question, context)
  features = tokenizer([input_text ], padding='max_length', truncation=True, max_length=512, return_tensors='pt')
  output = model.generate(input_ids=features['input_ids'].to(device), 
               attention_mask=features['attention_mask'].to(device))

  return tokenizer.decode(output[0], skip_special_tokens=True)
  
context = '''
La ex codirectora del grupo de investigación de IA ética de Google, Margaret Mitchell, 
quien fue despedida en febrero después de una controversia sobre un artículo crítico del que fue coautora, 
se unirá a HuggingFace para ayudar a que los algoritmos de IA sean más justos.
'''

question = '¿Qué hará Margaret Mitchell en HuggingFace?'

print(get_answer(context, question))

# ayudar a que los algoritmos de ia sean más justos
  
```

> Created by [Manuel Romero/@mrm8488](https://twitter.com/mrm8488) with the support of [Narrativa](https://www.narrativa.com/)

> Made with <span style="color: #e25555;">&hearts;</span> in Spain
