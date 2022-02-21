---
language: 
- fr

license: mit

datasets:
- MLSUM

pipeline_tag: "summarization"

widget:
- text: « La veille de l’ouverture, je vais faire venir un coach pour les salariés qui reprendront le travail. Cela va me coûter 300 euros, mais après des mois d’oisiveté obligatoire, la reprise n’est pas simple. Certains sont au chômage partiel depuis mars 2020 », raconte Alain Fontaine, propriétaire du restaurant Le Mesturet, dans le quartier de la Bourse, à Paris. Cette date d’ouverture, désormais, il la connaît. Emmanuel Macron a, en effet, donné le feu vert pour un premier accueil des clients en terrasse, mercredi 19 mai. M. Fontaine imagine même faire venir un orchestre ce jour-là pour fêter l’événement. Il lui reste toutefois à construire sa terrasse. Il pensait que les ouvriers passeraient samedi 1er mai pour l’installer, mais, finalement, le rendez-vous a été décalé. Pour l’instant, le tas de bois est entreposé dans la salle de restaurant qui n’a plus accueilli de convives depuis le 29 octobre 2020, quand le couperet de la fermeture administrative est tombé.M. Fontaine, président de l’Association française des maîtres restaurateurs, ne manquera pas de concurrents prêts à profiter de ce premier temps de réouverture des bars et restaurants. Même si le couvre-feu limite le service à 21 heures. D’autant que la Mairie de Paris vient d’annoncer le renouvellement des terrasses éphémères installées en 2020 et leur gratuité jusqu’à la fin de l’été.

tags:
- summarization
- mbart 
- bart
---

# Résumé automatique d'article de presses

Ce modèles est basé sur le modèle [`facebook/mbart-large-50`](https://huggingface.co/facebook/mbart-large-50) et été fine-tuné en utilisant des articles de presse issus de la base de données MLSUM. L'hypothèse à été faite que les chapeaux des articles faisaient de bon résumés de référence. 

## Entrainement

Nous avons testé deux architecture de modèles (T5 et BART) avec des textes en entrée de 512 ou 1024 tokens. Finallement c'est le modèle BART avec 512 tokens qui à été retenu.

Il a été entrainé sur 2 epochs (~700K articles) sur une Tesla V100 (32 heures d'entrainement).

## Résultats 

![Score de novelty](assets/novelty.png)  

Nous avons comparé notre modèle (`mbart-large-512-full` sur le graphique) à deux références:
 * MBERT qui correspond aux performances du modèle entrainé par l'équipe à l'origine de la base d'articles MLSUM
 * Barthez qui est un autre modèle basé sur des articles de presses issus de la base de données OrangeSum

 On voit que le score de novelty (cf papier MLSUM) de notre modèle n'est pas encore comparable à ces deux références et encore moins à une production humaine néanmoins les résumés générés sont dans l'ensemble de bonne qualité.

## Utilisation

```python
from transformers import AutoModelForSeq2SeqLM, AutoTokenizer
from transformers import SummarizationPipeline

model_name = 'lincoln/mbart-mlsum-automatic-summarization'

loaded_tokenizer = AutoTokenizer.from_pretrained(model_name)
loaded_model = AutoModelForSeq2SeqLM.from_pretrained(model_name)

nlp = SummarizationPipeline(model=loaded_model, tokenizer=loaded_tokenizer)
nlp("""
« La veille de l’ouverture, je vais faire venir un coach pour les salariés qui reprendront le travail. 
Cela va me coûter 300 euros, mais après des mois d’oisiveté obligatoire, la reprise n’est pas simple. 
Certains sont au chômage partiel depuis mars 2020 », raconte Alain Fontaine, propriétaire du restaurant Le Mesturet, 
dans le quartier de la Bourse, à Paris. Cette date d’ouverture, désormais, il la connaît. Emmanuel Macron a, en effet, 
donné le feu vert pour un premier accueil des clients en terrasse, mercredi 19 mai. M. Fontaine imagine même faire venir un orchestre ce jour-là pour fêter l’événement.  
Il lui reste toutefois à construire sa terrasse. Il pensait que les ouvriers passeraient samedi 1er mai pour l’installer, mais, finalement, le rendez-vous a été décalé. 
Pour l’instant, le tas de bois est entreposé dans la salle de restaurant qui n’a plus accueilli de convives depuis le 29 octobre 2020, 
quand le couperet de la fermeture administrative est tombé.M. Fontaine, président de l’Association française des maîtres restaurateurs, 
ne manquera pas de concurrents prêts à profiter de ce premier temps de réouverture des bars et restaurants. Même si le couvre-feu limite le service à 21 heures. 
D’autant que la Mairie de Paris vient d’annoncer le renouvellement des terrasses éphémères installées en 2020 et leur gratuité jusqu’à la fin de l’été.
""")
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