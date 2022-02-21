---
language: 
- fr

license: mit

datasets:
- MLSUM

pipeline_tag: "text-classification"

widget:
- text: La bourse de paris en forte baisse après que des canards ont envahit le parlement.

tags:
- text-classification
- flaubert 
---

# Classification d'articles de presses avec Flaubert

Ce modèle se base sur le modèle [`flaubert/flaubert_base_cased`](https://huggingface.co/flaubert/flaubert_base_cased) et à été fine-tuné en utilisant des articles de presse issus de la base de données MLSUM.  
Dans leur papier, les équipes de reciTAL et de la Sorbonne ont proposé comme ouverture de réaliser un modèle de détection de topic sur les articles de presse.

Les topics ont été extrait à partir des URL et nous avons effectué une étape de regroupement de topics pour éliminer ceux avec un trop faible volume et ceux qui paraissaient redondants.

Nous avons finalement utilisé la liste de topics avec les regroupements suivants:

* __Economie__: economie, argent, emploi, entreprises, economie-francaise, immobilier, crise-financiere, evasion-fiscale, economie-mondiale, m-voiture, smart-cities, automobile, logement, flottes-d-entreprise, import, crise-de-l-euro, guide-des-impots, le-club-de-l-economie, telephonie-mobile
* __Opinion__: idees, les-decodeurs, tribunes
* __Politique__: politique, election-presidentielle-2012, election-presidentielle-2017, elections-americaines, municipales, referendum-sur-le-brexit, elections-legislatives-2017, elections-regionales, donald-trump, elections-regionales-2015, europeennes-2014, elections-cantonales-2011, primaire-parti-socialiste, gouvernement-philippe, elections-departementales-2015, chroniques-de-la-presidence-trump, primaire-de-la-gauche, la-republique-en-marche, elections-americaines-mi-mandat-2018, elections, elections-italiennes, elections-senatoriales
* __Societe__: societe, sante, attaques-a-paris, immigration-et-diversite, religions, medecine, francaises-francais, mobilite
* __Culture__: televisions-radio, musiques, festival, arts, scenes, festival-de-cannes, mode, bande-dessinee, architecture, vins, photo, m-mode, fashion-week, les-recettes-du-monde, tele-zapping, critique-litteraire, festival-d-avignon, m-gastronomie-le-lieu, les-enfants-akira, gastronomie, culture, livres, cinema, actualite-medias, blog, m-gastronomie
* __Sport__: sport, football, jeux-olympiques, ligue-1, tennis, coupe-du-monde, mondial-2018, rugby, euro-2016, jeux-olympiques-rio-2016, cyclisme, ligue-des-champions, basket, roland-garros, athletisme, tour-de-france, euro2012, jeux-olympiques-pyeongchang-2018, coupe-du-monde-rugby, formule-1, voile, top-14, ski, handball, sports-mecaniques, sports-de-combat, blog-du-tour-de-france, sport-et-societe, sports-de-glisse, tournoi-des-6-nations
* __Environement__: planete, climat, biodiversite, pollution, energies, cop21
* __Technologie__: pixels, technologies, sciences, cosmos, la-france-connectee, trajectoires-digitales
* __Education__: campus, education, bac-lycee, enseignement-superieur, ecole-primaire-et-secondaire, o21, orientation-scolaire, brevet-college
* __Justice__: police-justice, panama-papers, affaire-penelope-fillon, documents-wikileaks, enquetes, paradise-papers

Les thèmes ayant moins de 100 articles n'ont pas été pris en compte.
Nous avons également mis de côté les articles faisant référence à des topics geographiques, ce qui a donné lieu à un nouveau modèle de classification.
Après nettoyage, la base MLSUM a été réduite à 293 995 articles. Le corps d'un article en moyenne comporte 694 tokens.

Nous avons entrainé le modèle sur 20% de la base nettoyée. En moyenne, le nombre d'articles par classe est de ~4K.

## Entrainement

Nous avons benchmarké différents modèles en les entrainant sur différentes parties des articles (titre, résumé, corps et titre+résumé) et avec des échantillons d'apprentissage de tailles différentes.

![Performance](./assets/Accuracy_cat.png)

Les modèles ont été entrainé sur le cloud Azure avec des Tesla V100.

## Modèle

Le modèle partagé sur HF est le modéle qui prend en entrée le corps d'un article. Nous l'avons entrainé sur 20% du jeu de donnée nettoyé.


## Résulats

![Matrice de confusion](assets/confusion_cat_m_0.2.png)  
*Les lignes correspondent aux labels prédits et les colonnes aux véritables topics. Les pourcentages sont calculés sur les colonnes.*  

_Nous garantissons pas les résultats sur le long terme. Modèle réalisé dans le cadre d'un POC._

## Utilisation

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
from transformers import TextClassificationPipeline

model_name = 'lincoln/flaubert-mlsum-topic-classification'

loaded_tokenizer = AutoTokenizer.from_pretrained(model_name)
loaded_model = AutoModelForSequenceClassification.from_pretrained(model_name)

nlp = TextClassificationPipeline(model=loaded_model, tokenizer=loaded_tokenizer)
nlp("Le Bayern Munich prend la grenadine.", truncation=True)
```

## Citation

```bibtex
@article{scialom2020mlsum,
      title={MLSUM: The Multilingual Summarization Corpus}, 
      author={Thomas Scialom and Paul-Alexis Dray and Sylvain Lamprier and Benjamin Piwowarski and Jacopo Staiano},
      year={2020},
      eprint={2004.14900},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```