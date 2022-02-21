---
language: 
- fr

license: mit

pipeline_tag: sentence-similarity

widget:
- source_sentence: "Bonsoir"
  sentences:
    - "Salut !"
    - "Hello"
    - "Bonsoir!"
    - "Bonsouar!"
    - "Bonsouar !"
    - "De rien"
    - "LUL LUL"
  example_title: "Coucou"
- source_sentence: "elle s'en sort bien"
  sentences:
    - "elle a raison"
    - "elle a tellement raison"
    - "Elle a pas tort"
    - "C'est bien ce qu'elle dit là"
    - "Hello"
  example_title: "Raison or not"
- source_sentence: "et la question énergétique n'est pas politique ?"
  sentences:
    - "C'est le nucléaire militaire qui a entaché le nucléaire pour l'énergie."
    - "La fusion nucléaire c'est pas pour maintenant malheureusement"
    - "le pro nucléaire redevient acceptable à gauche j'ai l'impression"
    - "La mer à Nantes?"
    - "c'est bien un olivier pour l'upr"
    - "Moi je vois juste sa lavallière"
  example_title: "Nucléaire"

tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
- twitch
- convbert
---


## Modèle de représentation d'un message Twitch à l'aide de ConvBERT

Modèle [sentence-transformers](https://www.SBERT.net): cela permet de mapper une séquence de texte en un vecteur numérique de dimension 256 et peut être utilisé pour des tâches de clustering ou de recherche sémantique.

L'expérimentation menée au sein de Lincoln avait pour principal objectif de mettre en œuvre des techniques NLP from scratch sur un corpus de messages issus d’un chat Twitch. Ces derniers sont exprimés en français, mais sur une plateforme internet avec le vocabulaire internet que cela implique (fautes, vocabulaire communautaires, abréviations, anglicisme, emotes, ...). 

Après avoir entrainé un modèle `ConvBert` puis `MLM` (cf section smodèles), nous avons entrainé un modèle _sentence-transformers_ à l'aide du framework d'apprentissage [SimCSE](https://www.sbert.net/examples/unsupervised_learning/SimCSE/README.html) en non supervisée. 

L'objectif est de spécialiser la moyenne des tokens _CLS_ de chaque token de la séquence pour représenter un vecteur numérique cohérent avec l'ensemble du corpus. _SimCSE_ crée fictivement des exemples positifs et négatifs supervisées à l'aide du dropout pour revenir à une tâche classique.

_Nous garantissons pas la stabilité du modèle sur le long terme. Modèle réalisé dans le cadre d'un POC._


## Usage (Sentence-Transformers)

Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:

```
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer
sentences = ["This is an example sentence", "Each sentence is converted"]

model = SentenceTransformer('2021twitchfr-conv-bert-small-mlm-simcse')
embeddings = model.encode(sentences)
print(embeddings)
```

## Semantic Textual Similarity

```python
from sentence_transformers import SentenceTransformer, models, util

# Two lists of sentences
sentences1 = ['zackFCZack',
              'Team bons petits plats',
              'sa commence a quelle heure de base popcorn ?',
              'BibleThump']

sentences2 = ['zack titulaire',
              'salade de pates c une dinguerie',
              'ça commence à être long la',
              'NotLikeThis']

# Compute embedding for both lists
embeddings1 = model.encode(sentences1, convert_to_tensor=True)
embeddings2 = model.encode(sentences2, convert_to_tensor=True)

# Compute cosine-similarits
cosine_scores = util.cos_sim(embeddings1, embeddings2)

# Output the pairs with their score
for i in range(len(sentences1)):
    print("Score: {:.4f} | \"{}\" -vs- \"{}\" ".format(cosine_scores[i][i], sentences1[i], sentences2[i]))
# Score: 0.5783 | "zackFCZack" -vs- "zack titulaire" 
# Score: 0.2881 | "Team bons petits plats" -vs- "salade de pates c une dinguerie" 
# Score: 0.4529 | "sa commence a quelle heure de base popcorn ?" -vs- "ça commence à être long la" 
# Score: 0.5805 | "BibleThump" -vs- "NotLikeThis" 

```

## Entrainement

* 500 000 messages twitchs échantillonnés (cf description données des modèles de bases)
* Batch size: 24
* Epochs: 24
* Loss: MultipleNegativesRankingLoss

_A noter:_ 
* _ConvBert a été entrainé avec un longueur de 128 tokens max, mais est utilisé pour 512 dans ce modèle. Pas de problème._
* _La loss d'apprentissage n'est pas encore disponible: peu de visibilité sur les performances._

L'ensemble du code d'entrainement sur le github public [lincoln/twitchatds](https://github.com/Lincoln-France/twitchatds).

## Application:

Nous avons utilisé une approche détournée de [BERTopic](https://maartengr.github.io/BERTopic/) pour réaliser un clustering d'un stream en prenant en compte la dimension temporelle: i.e. le nombre de seconde écoulée depuis le début du stream.

![approche_bertopic_lincoln](assets/approche_lincoln_topic_clustering_twitch.jpg)

Globalement, l'approche donnes des résultats satisfaisant pour identifier des messages dit "similaires" récurrents. L'approche en revanche est fortement influencée par la ponctuation et la structure d'un message. Cela est largement explicable par le manque d'entrainement de l'ensemble des modèles et une volumétrie faible.

### Clustering émission "Backseat":

Entre 19h30 et 20h00:

![1930_2000](./assets/scale_600_1930_2000.png)

🎞️ en vidéo: [youtu.be/EcjvlE9aTls](https://youtu.be/EcjvlE9aTls)

### Exemple regroupement émission "PopCorn":

```txt
-------------------- LABEL 106 --------------------
circus (0.88)/sulli (0.23)/connu (0.19)/jure (0.12)/aime (0.11)
silouhette moyenne: 0.04
-------------------- LABEL 106 --------------------
2021-03-30 20:10:22  0.01: les gosse c est des animaux 
2021-03-30 20:12:11 -0.03: oue c connu 
2021-03-30 20:14:15  0.03: oh le circus !! <3 
2021-03-30 20:14:19  0.12: le circus l'anciennnee 
2021-03-30 20:14:22  0.06: jure le circus ! 
2021-03-30 20:14:27 -0.03: le sulli 
2021-03-30 20:14:31  0.09: le circus??? j'aime po 
2021-03-30 20:14:34  0.11: le Circus, hors de prix ! 
2021-03-30 20:14:35 -0.09: le Paddock a Rignac en Aveyron 
2021-03-30 20:14:39  0.11: le circus >< 
2021-03-30 20:14:39  0.04: le Titty Twister de Besançon 

-------------------- LABEL 17 --------------------
pates (0.12)/riz (0.09)/pâtes (0.09)/salade (0.07)/emission (0.07)
silouhette moyenne: -0.05
-------------------- LABEL 17 --------------------
2021-03-30 20:11:18 -0.03: Des nanimaux trop beaux ! 
2021-03-30 20:13:11 -0.01: episode des simpsons ça... 
2021-03-30 20:13:41 -0.01: des le debut d'emission ca tue mdrrrrr 
2021-03-30 20:13:50  0.03: des "lasagnes" 
2021-03-30 20:14:37 -0.18: poubelle la vie 
2021-03-30 20:15:13  0.03: Une omelette 
2021-03-30 20:15:35 -0.19: salade de bite 
2021-03-30 20:15:36 -0.00: hahaha ce gastronome 
2021-03-30 20:15:43 -0.08: salade de pates c une dinguerie 
2021-03-30 20:17:00 -0.11: Une bonne femme ! 
2021-03-30 20:17:06 -0.05: bouffe des graines 
2021-03-30 20:17:08 -0.06: des pokeball ? 
2021-03-30 20:17:11 -0.12: le choux fleur cru 
2021-03-30 20:17:15  0.05: des pockeball ? 
2021-03-30 20:17:27 -0.00: du chou fleur crue 
2021-03-30 20:17:36 -0.09: un râgout de Meynia !!!! 
2021-03-30 20:17:43 -0.07: une line up Sa rd o ch Zack Ponce my dream 
2021-03-30 20:17:59 -0.10: Pâtes/10 
2021-03-30 20:18:09 -0.05: Team bons petits plats 
2021-03-30 20:18:13 -0.10: pate level 
2021-03-30 20:18:19 -0.03: que des trucs très basiques 
2021-03-30 20:18:24  0.03: des pates et du jambon c'est de la cuisine? 
2021-03-30 20:18:30  0.05: Des pates et du riz ouai 
2021-03-30 20:18:37 -0.02: des gnocchis à la poele c'est cuisiner ? 
2021-03-30 20:18:50 -0.03: Pâtes à pizzas, pulled pork, carbonade flamande, etc.. 
2021-03-30 20:19:01 -0.11: Des pâtes ou du riz ça compte ? 
2021-03-30 20:19:22 -0.21: le noob 
2021-03-30 20:19:47 -0.02: Une bonne escalope de milanaise les gars 
2021-03-30 20:20:05 -0.04: faites des gratins et des quiches 

-------------------- LABEL 67 --------------------
1 1 (0.25)/1 (0.19)/ (0.0)/ (0.0)/ (0.0)
silouhette moyenne: 0.96
-------------------- LABEL 67 --------------------
2021-03-30 20:24:17  0.94: +1 
2021-03-30 20:24:37  0.97: +1 
2021-03-30 20:24:37  0.97: +1 
2021-03-30 20:24:38  0.97: +1 
2021-03-30 20:24:39  0.97: +1 
2021-03-30 20:24:43  0.97: +1 
2021-03-30 20:24:44  0.97: +1 
2021-03-30 20:24:47  0.97: +1 
2021-03-30 20:24:49  0.97: +1 
2021-03-30 20:25:00  0.97: +1 
2021-03-30 20:25:21  0.95: +1 
2021-03-30 20:25:25  0.95: +1 
2021-03-30 20:25:28  0.94: +1 
2021-03-30 20:25:30  0.94: +1 
```

## Full Model Architecture

```
SentenceTransformer(
  (0): Transformer({'max_seq_length': 512, 'do_lower_case': False}) with Transformer model: ConvBertModel 
  (1): Pooling({'word_embedding_dimension': 256, 'pooling_mode_cls_token': True, 'pooling_mode_mean_tokens': False, 'pooling_mode_max_tokens': False, 'pooling_mode_mean_sqrt_len_tokens': False})
)
```

## Modèles:

* [2021twitchfr-conv-bert-small](https://huggingface.co/lincoln/2021twitchfr-conv-bert-small)
* [2021twitchfr-conv-bert-small-mlm](https://huggingface.co/lincoln/2021twitchfr-conv-bert-small-mlm)
* [2021twitchfr-conv-bert-small-mlm-simcse](https://huggingface.co/lincoln/2021twitchfr-conv-bert-small-mlm-simcse)