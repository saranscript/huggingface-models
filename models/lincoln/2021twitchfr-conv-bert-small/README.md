---
language: 
- fr

license: mit

pipeline_tag: "feature-extraction"

widget:
- text: LUL +1 xD La Fronce !

tags:
- feature-extraction
- convbert
- twitch 
---

## Modèle de langue sur les données Twitch FR

L'expérimentation menée au sein de Lincoln avait pour principal objectif de mettre en œuvre des techniques NLP from scratch sur un corpus de messages issus d’un chat Twitch. Ces derniers sont exprimés en français, mais sur une plateforme internet avec le vocabulaire internet que cela implique (fautes, vocabulaire communautaires, abréviations, anglicisme, emotes, ...). 

Nos contraintes sont celles d’une entreprise n’ayant pas une volumétrie excessive de données et une puissance infinie de calcul.
Il a été nécessaire de construire un nouveau tokenizer afin de mieux correspondre à notre corpus plutôt qu’un tokenizer français existant.

Note corpus étant faible en volumétrie par rapport aux données habituelles pour entrainer un modèle BERT, nous avons opté pour l’entrainement d’un modèle dit « small ». Et il a été montré dans la littérature qu’un corpus de quelques giga octets peut donner de bons résultats, c’est pourquoi nous avons continué avec notre corpus.

La limite de la puissance de calcul a été contourné à l’aide d’une nouvelle architecture d’apprentissage basée sur un double modèle générateur / discriminateur. 

Ceci nous a permis d’entrainer un modèle de langue ConvBERT sur nos données, ainsi qu’un modèle de masking en quelques heures sur une carte GPU V100. 

_Nous garantissons pas la stabilité du modèle sur le long terme. Modèle réalisé dans le cadre d'un POC._

## Données

| Streamer                                      | Nbr de messages | Categories notables en 2021        |
| --------------------------------------------- | --------------- | ---------------------------------- |
| Ponce                                         | 2 604 935       | Chatting/Mario Kart/FIFA           |
| Domingo                           | 1 209 703       | Chatting/talk-shows/FM2O21         |
| Mistermv                                      | 1 205 882       | Isaac/Special events/TFT           |
| Zerator                                       | 900 894         | New World/WOW/Valorant             |
| Blitzstream                                   | 821 585         | Chess                              |
| Squeezie                                      | 602 148         | Chatting / Minecraft               |
| Antoinedaniellive                             | 548 497         | Geoguessr                          |
| Jeanmassietaccropolis/jeanmassiet | 301 387         | Talk-shows/chatting/special events |
| Samueletienne                                 | 215 956         | chatting                           |

Sur la période du 12/03/2021 au 22/07/2021. La totalité des messages comptent 9 410 987 messages sur ces neufs streamers. Ces messages sont issus du canal IRC, donc n’ont pas subi de modération

Les données d'entrainement sont basé sur le format d'entrainement du modèle ELECTRA. Cela nécessite de formater les données en paragraphe, séparés par phrase. Nous avons choisi de regrouper les messages dans une fenêtre de 60 secondes, faisant office de paragraphe, avec les conditions suivantes :
*  Longueur supérieure à 170 (ce qui représente en moyenne 50 tokens) afin de ne pas créer des instances ayant pas d’information car majoritairement vide : un padding sera nécessaire et pénalise la vitesse d’apprentissage.
* 128 tokens maximums (défaut)

Si la longueur maximale est atteinte, une deuxième instance est créée. Au final, la volumétrie d'instance d'entrainement est de 554 974.
 

## Application

Voir github public [lincoln/twitchatds](https://github.com/Lincoln-France/twitchatds) pour les détails d'implémentation et les résultats.

## Remarques

* Expérimentation ponctuelle
* Les métriques d'entrainement sont disponibles dans l'onglet _Training metrics_
* Pour une meilleure stabilité, les données doivent être plus hétérogènes et volumineuse. Le modèle doit être entrainé + de 24h. 

## Usage

```python
from transformers import AutoTokenizer, ConvBertModel 
from transformers import FeatureExtractionPipeline

model_name = 'lincoln/2021twitchfr-conv-bert-small'

loaded_tokenizer = AutoTokenizer.from_pretrained(model_name)
loaded_model = ConvBertModel.from_pretrained(model_name)

nlp = FeatureExtractionPipeline(model=loaded_model, tokenizer=loaded_tokenizer)
nlp("<3 <3 les modos")
```

## Modèles:

* [2021twitchfr-conv-bert-small](https://huggingface.co/lincoln/2021twitchfr-conv-bert-small)
* [2021twitchfr-conv-bert-small-mlm](https://huggingface.co/lincoln/2021twitchfr-conv-bert-small-mlm)
* [2021twitchfr-conv-bert-small-mlm-simcse](https://huggingface.co/lincoln/2021twitchfr-conv-bert-small-mlm-simcse)

