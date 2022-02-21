---
language:
- da
license: mit
tags:
- generated_from_trainer
model-index:
- name: xlmr-base-texas-squad-da
  results: []
widget:
- text: "Hvem handler artiklen om?"
  context: "Forfatter og musiker Flemming Quist Møller er død i en alder af 79 år. Den folkekære kunstner faldt om ved morgenbordet med en blodprop i hjertet i mandags. Det kunne forfatterens søn, Carl Quist-Møller, bekræfte over for TV 2 Lorry.- Han faldt om i det hus i Taarbæk, hvor han er vokset op og også har boet de sidste år af sit liv. Han blev lagt i koma på Rigshospitalet. Her har vi siddet omkring ham i en uge, siger Carl Quist-Møller til mediet.MindeordI mange år var Flemming Quist Møller en del af bandet Bazaar sammen med Peter Bastian, Anders Koppel og Mehmet Ozan.Anders Koppel er tydeligt rørt over vennens død, da Ekstra Bladet rækker ud til ham mandag aften.- Det er en stor del af mit liv, der er forsvundet med Flemmings liv, det er klart. Vi har spillet sammen i 37 år, siger han og fortsætter:- Jeg vil mest huske ham for hans ukonventionelle tilgang til alting. Flemming havde et meget stærkt blik for det autentiske og ærlige. Han var ikke bundet af normer -tværtimod, hvis han så en norm, hvor noget skulle gøres på en bestemt måde, så flygtede han eller prøvede at springe det i stumper og stykker.Ifølge den danske musiker og komponist er netop følgende ord rammende for Flemming Quist Møller: Original, vidende, kompromisløs og humoristisk."
---

# TExAS-SQuAD-da

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on the TExAS-SQuAD-da dataset.
It achieves the following results on the evaluation set:
- Exact match: 63.96%
- F1-score: 68.40%

In comparison, the `jacobshein/danish-bert-botxo-qa-squad` model achieves 30.37% EM and 37.15% F1.

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 1.6438        | 1.0   | 4183  | 1.4711          |
| 1.4079        | 2.0   | 8366  | 1.4356          |
| 1.2532        | 3.0   | 12549 | 1.4509          |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.8.1+cu101
- Datasets 1.12.1
- Tokenizers 0.10.3
