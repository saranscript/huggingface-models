---
language: 
  - fr

license: mit

datasets:
  - squadFR
  - fquad
  - piaf

tags:
  - camembert
  - answer extraction 
---

# Extraction de réponse

Ce modèle est _fine tuné_ à partir du modèle [camembert-base](https://huggingface.co/camembert-base) pour la tâche de classification de tokens. 
L'objectif est d'identifier les suites de tokens probables qui pourrait être l'objet d'une question.


## Données d'apprentissage

La base d'entrainement est la concatenation des bases SquadFR, [fquad](https://huggingface.co/datasets/fquad), [piaf](https://huggingface.co/datasets/piaf). 
Les réponses de chaque contexte ont été labelisées avec le label "ANS". 

Volumétrie (nombre de contexte):
* train: 24 652
* test: 1 370
* valid: 1 370


## Entrainement

L'apprentissage s'est effectué sur une carte Tesla K80.

* Batch size: 16
* Weight decay: 0.01
* Learning rate: 2x10-5 (décroit linéairement)
* Paramètres par défaut de la classe [TrainingArguments](https://huggingface.co/transformers/main_classes/trainer.html#trainingarguments)
* Total steps: 1 000

Le modèle semble sur apprendre au delà :

![Loss](assets/loss_m_sl_sota_2.PNG)  


## Critiques

Le modèle n'a pas de bonnes performances et doit être corrigé après prédiction pour être cohérent. La tâche de classification n'est pas évidente car le modèle doit identifier des groupes de token _sachant_ qu'une question peut être posée.

![Performances](assets/perfs_m_sl_sota_2.PNG)

## Utilisation

_Le modèle est un POC, nous garantissons pas ses performances_

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
import numpy as np

model_name = "lincoln/camembert-squadFR-fquad-piaf-answer-extraction"

loaded_tokenizer = AutoTokenizer.from_pretrained(model_path)
loaded_model = AutoModelForTokenClassification.from_pretrained(model_path)
text = "La science des données est un domaine interdisciplinaire qui utilise des méthodes, des processus,\
    des algorithmes et des systèmes scientifiques pour extraire des connaissances et des idées de nombreuses données structurelles et non structurées.\
        Elle est souvent associée aux données massives et à l'analyse des données."

inputs = loaded_tokenizer(text, return_tensors="pt", return_offsets_mapping=True)
outputs = loaded_model(inputs.input_ids).logits
probs = 1 / (1 + np.exp(-outputs.detach().numpy()))
probs[:, :, 1][0] = np.convolve(probs[:, :, 1][0], np.ones(2), 'same') / 2

sentences = loaded_tokenizer.tokenize(text, add_special_tokens=False)
prob_answer_tokens = probs[:, 1:-1, 1].flatten().tolist()
offset_start_mapping = inputs.offset_mapping[:, 1:-1, 0].flatten().tolist()
offset_end_mapping = inputs.offset_mapping[:, 1:-1, 1].flatten().tolist()
threshold = 0.4

entities = []
for ix, (token, prob_ans, offset_start, offset_end) in enumerate(zip(sentences, prob_answer_tokens, offset_start_mapping, offset_end_mapping)):
    entities.append({
        'entity': 'ANS' if prob_ans > threshold else 'O',
        'score': prob_ans, 
        'index': ix,
        'word': token,
        'start': offset_start,
        'end': offset_end
    })

for p in entities:
    print(p)

# {'entity': 'O', 'score': 0.3118681311607361, 'index': 0, 'word': '▁La', 'start': 0, 'end': 2}
# {'entity': 'O', 'score': 0.37866950035095215, 'index': 1, 'word': '▁science', 'start': 3, 'end': 10}
# {'entity': 'ANS', 'score': 0.45018652081489563, 'index': 2, 'word': '▁des', 'start': 11, 'end': 14}
# {'entity': 'ANS', 'score': 0.4615934491157532, 'index': 3, 'word': '▁données', 'start': 15, 'end': 22}
# {'entity': 'O', 'score': 0.35033443570137024, 'index': 4, 'word': '▁est', 'start': 23, 'end': 26}
# {'entity': 'O', 'score': 0.24779987335205078, 'index': 5, 'word': '▁un', 'start': 27, 'end': 29}
# {'entity': 'O', 'score': 0.27084410190582275, 'index': 6, 'word': '▁domaine', 'start': 30, 'end': 37}
# {'entity': 'O', 'score': 0.3259460926055908, 'index': 7, 'word': '▁in', 'start': 38, 'end': 40}
# {'entity': 'O', 'score': 0.371802419424057, 'index': 8, 'word': 'terdisciplinaire', 'start': 40, 'end': 56}
# {'entity': 'O', 'score': 0.3140853941440582, 'index': 9, 'word': '▁qui', 'start': 57, 'end': 60}
# {'entity': 'O', 'score': 0.2629334330558777, 'index': 10, 'word': '▁utilise', 'start': 61, 'end': 68}
# {'entity': 'O', 'score': 0.2968383729457855, 'index': 11, 'word': '▁des', 'start': 69, 'end': 72}
# {'entity': 'O', 'score': 0.33898216485977173, 'index': 12, 'word': '▁méthodes', 'start': 73, 'end': 81}
# {'entity': 'O', 'score': 0.3776060938835144, 'index': 13, 'word': ',', 'start': 81, 'end': 82}
# {'entity': 'O', 'score': 0.3710060119628906, 'index': 14, 'word': '▁des', 'start': 83, 'end': 86}
# {'entity': 'O', 'score': 0.35908180475234985, 'index': 15, 'word': '▁processus', 'start': 87, 'end': 96}
# {'entity': 'O', 'score': 0.3890596628189087, 'index': 16, 'word': ',', 'start': 96, 'end': 97}
# {'entity': 'O', 'score': 0.38341325521469116, 'index': 17, 'word': '▁des', 'start': 101, 'end': 104}
# {'entity': 'O', 'score': 0.3743852376937866, 'index': 18, 'word': '▁', 'start': 105, 'end': 106}
# {'entity': 'O', 'score': 0.3943936228752136, 'index': 19, 'word': 'algorithme', 'start': 105, 'end': 115}
# {'entity': 'O', 'score': 0.39456743001937866, 'index': 20, 'word': 's', 'start': 115, 'end': 116}
# {'entity': 'O', 'score': 0.3846966624259949, 'index': 21, 'word': '▁et', 'start': 117, 'end': 119}
# {'entity': 'O', 'score': 0.367380827665329, 'index': 22, 'word': '▁des', 'start': 120, 'end': 123}
# {'entity': 'O', 'score': 0.3652925491333008, 'index': 23, 'word': '▁systèmes', 'start': 124, 'end': 132}
# {'entity': 'O', 'score': 0.3975735306739807, 'index': 24, 'word': '▁scientifiques', 'start': 133, 'end': 146}
# {'entity': 'O', 'score': 0.36417365074157715, 'index': 25, 'word': '▁pour', 'start': 147, 'end': 151}
# {'entity': 'O', 'score': 0.32438698410987854, 'index': 26, 'word': '▁extraire', 'start': 152, 'end': 160}
# {'entity': 'O', 'score': 0.3416857123374939, 'index': 27, 'word': '▁des', 'start': 161, 'end': 164}
# {'entity': 'O', 'score': 0.3674810230731964, 'index': 28, 'word': '▁connaissances', 'start': 165, 'end': 178}
# {'entity': 'O', 'score': 0.38362061977386475, 'index': 29, 'word': '▁et', 'start': 179, 'end': 181}
# {'entity': 'O', 'score': 0.364640474319458, 'index': 30, 'word': '▁des', 'start': 182, 'end': 185}
# {'entity': 'O', 'score': 0.36050117015838623, 'index': 31, 'word': '▁idées', 'start': 186, 'end': 191}
# {'entity': 'O', 'score': 0.3768993020057678, 'index': 32, 'word': '▁de', 'start': 192, 'end': 194}
# {'entity': 'O', 'score': 0.39184248447418213, 'index': 33, 'word': '▁nombreuses', 'start': 195, 'end': 205}
# {'entity': 'ANS', 'score': 0.4091200828552246, 'index': 34, 'word': '▁données', 'start': 206, 'end': 213}
# {'entity': 'ANS', 'score': 0.41234123706817627, 'index': 35, 'word': '▁structurelle', 'start': 214, 'end': 226}
# {'entity': 'ANS', 'score': 0.40243157744407654, 'index': 36, 'word': 's', 'start': 226, 'end': 227}
# {'entity': 'ANS', 'score': 0.4007353186607361, 'index': 37, 'word': '▁et', 'start': 228, 'end': 230}
# {'entity': 'ANS', 'score': 0.40597623586654663, 'index': 38, 'word': '▁non', 'start': 231, 'end': 234}
# {'entity': 'ANS', 'score': 0.40272021293640137, 'index': 39, 'word': '▁structurée', 'start': 235, 'end': 245}
# {'entity': 'O', 'score': 0.392631471157074, 'index': 40, 'word': 's', 'start': 245, 'end': 246}
# {'entity': 'O', 'score': 0.34266412258148193, 'index': 41, 'word': '.', 'start': 246, 'end': 247}
# {'entity': 'O', 'score': 0.26178646087646484, 'index': 42, 'word': '▁Elle', 'start': 255, 'end': 259}
# {'entity': 'O', 'score': 0.2265639454126358, 'index': 43, 'word': '▁est', 'start': 260, 'end': 263}
# {'entity': 'O', 'score': 0.22844195365905762, 'index': 44, 'word': '▁souvent', 'start': 264, 'end': 271}
# {'entity': 'O', 'score': 0.2475772500038147, 'index': 45, 'word': '▁associée', 'start': 272, 'end': 280}
# {'entity': 'O', 'score': 0.3002186715602875, 'index': 46, 'word': '▁aux', 'start': 281, 'end': 284}
# {'entity': 'O', 'score': 0.3875720798969269, 'index': 47, 'word': '▁données', 'start': 285, 'end': 292}
# {'entity': 'ANS', 'score': 0.445063054561615, 'index': 48, 'word': '▁massive', 'start': 293, 'end': 300}
# {'entity': 'ANS', 'score': 0.4419114589691162, 'index': 49, 'word': 's', 'start': 300, 'end': 301}
# {'entity': 'ANS', 'score': 0.4240635633468628, 'index': 50, 'word': '▁et', 'start': 302, 'end': 304}
# {'entity': 'O', 'score': 0.3900952935218811, 'index': 51, 'word': '▁à', 'start': 305, 'end': 306}
# {'entity': 'O', 'score': 0.3784807324409485, 'index': 52, 'word': '▁l', 'start': 307, 'end': 308}
# {'entity': 'O', 'score': 0.3459452986717224, 'index': 53, 'word': "'", 'start': 308, 'end': 309}
# {'entity': 'O', 'score': 0.37636008858680725, 'index': 54, 'word': 'analyse', 'start': 309, 'end': 316}
# {'entity': 'ANS', 'score': 0.4475618302822113, 'index': 55, 'word': '▁des', 'start': 317, 'end': 320}
# {'entity': 'ANS', 'score': 0.43845775723457336, 'index': 56, 'word': '▁données', 'start': 321, 'end': 328}
# {'entity': 'O', 'score': 0.3761221170425415, 'index': 57, 'word': '.', 'start': 328, 'end': 329}
```
