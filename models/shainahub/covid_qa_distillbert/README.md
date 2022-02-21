---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- covid_qa_deepset
metrics:
- squad_v2  # Example: wer. Use metric id from https://hf.co/metrics
widget:
- text: "What is COVID-19?"
  context: "Coronavirus disease 2019 (COVID-19) is a contagious disease caused by severe acute respiratory syndrome coronavirus 2 (SARS-CoV-2). The first known case was identified in Wuhan, China, in December 2019.[7] The disease has since spread worldwide, leading to an ongoing pandemic."
- text: "Where was COVID-19 first discovered?"
  context: "The first known infections from SARS-CoV-2 were discovered in Wuhan, China. The original source of viral transmission to humans remains unclear, as does whether the virus became pathogenic before or after the spillover event."
- text: "What is Post-COVID syndrome?"
  context: "Long COVID, also known as post-COVID-19 syndrome, post-acute sequelae of COVID-19 (PASC), or chronic COVID syndrome (CCS) is a condition characterized by long-term sequelae appearing or persisting after the typical convalescence period of COVID-19. Long COVID can affect nearly every organ system, with sequelae including respiratory system disorders, nervous system and neurocognitive disorders, mental health disorders, metabolic disorders, cardiovascular disorders, gastrointestinal disorders, malaise, fatigue, musculoskeletal pain, and anemia. A wide range of symptoms are commonly reported, including fatigue, headaches, shortness of breath, anosmia (loss of smell), parosmia (distorted smell), muscle weakness, low fever and cognitive dysfunction."

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-squad

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the covid_qa_deepset dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0976

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 0.2502        | 1.0   | 3880  | 0.1824          |
| 0.2007        | 2.0   | 7760  | 0.1250          |
| 0.1338        | 3.0   | 11640 | 0.0976          |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
