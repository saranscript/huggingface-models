---
language: es
tags:
- Long documents
- LongFormer
- QA
- Q&A
datasets:
- BSC-TeMU/SQAC

---

# Spanish Longformer fine-tuned on **SQAC** for Spanish **QA** 📖❓
[longformer-base-4096-spanish](https://huggingface.co/mrm8488/longformer-base-4096-spanish) fine-tuned on [SQAC](https://huggingface.co/datasets/BSC-TeMU/SQAC) for **Q&A** downstream task.

## Details of the model 🧠
[longformer-base-4096-spanish](https://huggingface.co/mrm8488/longformer-base-4096-spanish) is a BERT-like model started from the RoBERTa checkpoint (**BERTIN** in this case) and pre-trained for *MLM* on long documents (from BETO's `all_wikis`). It supports sequences of length up to **4,096**! 

## Details of the dataset 📚 

This dataset contains 6,247 contexts and 18,817 questions with their answers, 1 to 5 for each fragment.
The sources of the contexts are:
* Encyclopedic articles from [Wikipedia in Spanish](https://es.wikipedia.org/), used under [CC-by-sa licence](https://creativecommons.org/licenses/by-sa/3.0/legalcode). 
* News from [Wikinews in Spanish](https://es.wikinews.org/), used under [CC-by licence](https://creativecommons.org/licenses/by/2.5/). 
* Text from the Spanish corpus [AnCora](http://clic.ub.edu/corpus/en), which is a mix from diferent newswire and literature sources, used under [CC-by licence](https://creativecommons.org/licenses/by/4.0/legalcode). 
This dataset can be used to build extractive-QA.

## Evaluation Metrics 📈

TBA

## Fast Usage with HF `pipeline` 🧪
```py
from transformers import pipeline
qa_pipe = pipeline("question-answering", model='mrm8488/longformer-base-4096-spanish-finetuned-squad')
context = '''
Hace aproximadamente un año, Hugging Face, una startup de procesamiento de lenguaje natural con sede en Brooklyn, Nueva York, lanzó BigScience, un proyecto internacional con más de 900 investigadores que está diseñado para comprender mejor y mejorar la calidad de los grandes modelos de lenguaje natural. Los modelos de lenguaje grande (LLM), algoritmos que pueden reconocer, predecir y generar lenguaje sobre la base de conjuntos de datos basados ​​en texto, han captado la atención de empresarios y entusiastas de la tecnología por igual. Pero el costoso hardware requerido para desarrollar LLM los ha mantenido en gran medida fuera del alcance de los investigadores sin los recursos de compañías como OpenAI y DeepMind detrás de ellos.

Inspirándose en organizaciones como la Organización Europea para la Investigación Nuclear (también conocida como CERN) y el Gran Colisionador de Hadrones, el objetivo de BigScience es crear LLM y grandes conjuntos de datos de texto que eventualmente serán de código abierto para la IA más amplia. comunidad. Los modelos serán entrenados en la supercomputadora Jean Zay ubicada cerca de París, Francia, que se encuentra entre las máquinas más poderosas del mundo.
'''
question = "¿Cuál es el objetivo de BigScience?"

qa_pipe({'context':context, 'question': question})
# It outpus
```
```js
{'answer': 'comprender mejor y mejorar la calidad de los grandes modelos de lenguaje natural.',
 'end': 305,
 'score': 0.9999799728393555,
 'start': 224}
 ```
 
 > Created by [Manuel Romero/@mrm8488](https://twitter.com/mrm8488) with the support of [Narrativa](https://www.narrativa.com/)

> Made with <span style="color: #e25555;">&hearts;</span> in Spain
