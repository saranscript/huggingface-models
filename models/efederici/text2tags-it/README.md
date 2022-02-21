---
language: 
  - it
tags:
- summarization
- tags
- Italian
inference:
  parameters:
    do_sample: False
    min_length: 0
widget:
  - text: "Nel 1924 la scrittrice Virginia Woolf affrontò nel saggio Mr Bennett e Mrs Brown il tema della costruzione e della struttura del romanzo, genere all’epoca considerato in declino a causa dell’incapacità degli autori e delle autrici di creare personaggi realistici. Woolf raccontò di aver a lungo osservato, durante un viaggio in treno da Richmond a Waterloo, una signora di oltre 60 anni seduta davanti a lei, chiamata signora Brown. Ne rimase affascinata, per la capacità di quella figura di evocare storie possibili e fare da spunto per un romanzo: «tutti i romanzi cominciano con una vecchia signora seduta in un angolo». Immagini come quella della signora Brown, secondo Woolf, «costringono qualcuno a cominciare, quasi automaticamente, a scrivere un romanzo». Nel saggio Woolf provò ad analizzare le tecniche narrative utilizzate da tre noti scrittori inglesi dell’epoca – H. G. Wells, John Galsworthy e Arnold Bennett – per comprendere perché le convenzioni stilistiche dell’Ottocento risultassero ormai inadatte alla descrizione dei «caratteri» umani degli anni Venti. In un lungo e commentato articolo del New Yorker, la critica letteraria e giornalista Parul Sehgal, a lungo caporedattrice dell’inserto culturale del New York Times dedicato alle recensioni di libri, ha provato a compiere un esercizio simile a quello di Woolf, chiedendosi come gli autori e le autrici di oggi tratterebbero la signora Brown. E ha immaginato che probabilmente quella figura non eserciterebbe su di loro una curiosità e un fascino legati alla sua incompletezza e al suo aspetto misterioso, ma con ogni probabilità trasmetterebbe loro l’indistinta e generica impressione di aver subìto un trauma."
    example_title: "Virginia Woolf"
  - text: "I lavori di ristrutturazione dell’interno della cattedrale di Notre-Dame a Parigi, seguiti al grande incendio che nel 2019 bruciò la guglia e buona parte del tetto, sono da settimane al centro di un acceso dibattito sui giornali francesi per via di alcune proposte di rinnovamento degli interni che hanno suscitato critiche e allarmi tra esperti e opinionisti conservatori. Il progetto ha ricevuto una prima approvazione dalla commissione nazionale competente, ma dovrà ancora essere soggetto a varie revisioni e ratifiche che coinvolgeranno tecnici e politici locali e nazionali, fino al presidente Emmanuel Macron. Ma le modifiche previste al sistema di viabilità per i visitatori, all’illuminazione, ai posti a sedere e alle opere d’arte che si vorrebbero esporre hanno portato alcuni critici a parlare di «parco a tema woke» e «Disneyland del politicamente corretto»."
    example_title: "Notre-Dame"
---

# text2tags-it

The model has been trained on a collection of 28k news articles with tags. Its purpose is to create tags suitable for the given article.

### Usage 

Sample code with an article from IlPost:

```python
from transformers import T5ForConditionalGeneration,T5Tokenizer

model = T5ForConditionalGeneration.from_pretrained("efederici/text2tags-it")
tokenizer = T5Tokenizer.from_pretrained("efederici/text2tags-it")

article = '''
Da bambino era preoccupato che al mondo non ci fosse più nulla da scoprire. Ma i suoi stessi studi gli avrebbero dato torto: insieme a James Watson, nel 1953 Francis Crick strutturò il primo modello di DNA, la lunga sequenza di codici che identifica ogni essere vivente, rendendolo unico e diverso da tutti gli altri. 
La scoperta gli valse il Nobel per la Medicina. È uscita in queste settimane per Codice la sua biografia, Francis Crick — Lo scopritore del DNA, scritta da Matt Ridley, che racconta vita e scienza dell'uomo che capì perché siamo fatti così.
'''

def tag(text: str):
    """ Generates tags from given text """
    text = text.strip().replace('\n', '')
    text = 'summarize: ' + text
    tokenized_text = tokenizer.encode(text, return_tensors="pt")

    tags_ids = model.generate(tokenized_text,
                                        num_beams=4,
                                        no_repeat_ngram_size=2,
                                        max_length=20,
                                        early_stopping=True)

    output = tokenizer.decode(tags_ids[0], skip_special_tokens=True)
    return output.split(', ')

tags = tag(article)
print(tags)
```

### Overview

- Model: T5 ([it5-small](https://huggingface.co/gsarti/it5-small))
- Language: Italian
- Downstream-task: Summarization (for topic tagging)
- Training data: Custom dataset
- Code: See example
- Infrastructure: 1x T4