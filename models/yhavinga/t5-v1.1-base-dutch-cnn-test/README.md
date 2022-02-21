---
language:
- nl
datasets:
- yhavinga/mc4_nl_cleaned
- ml6team/cnn_dailymail_nl
tags:
- summarization
- t5
- seq2seq
license: apache-2.0
pipeline_tag: summarization
widget:
- text: "Het Van Goghmuseum in Amsterdam heeft vier kostbare prenten verworven van Mary Cassatt, de Amerikaanse impressionistische kunstenaar en tijdgenoot van Vincent van Gogh. Dat heeft het museum woensdagmiddag op een persconferentie bekendgemaakt. Het gaat om drie grote kleurenetsen en een zwart-wit litho met voorstellingen van vrouwen. Voor deze prenten, die afkomstig zijn van een Amerikaanse verzamelaar, betaalde het museum ruim 1,4 miljoen euro. Drie grote fondsen en een aantal particulieren hebben samen de aankoopsom beschikbaar gesteld. Mary Stevenson Cassatt (1844-1926) woonde en werkte lange tijd in Frankrijk. Ze staat met haar impressionistische schilderijen en tekeningen te boek als een van de vernieuwers van de Parijse kunstwereld in de late negentiende eeuw. Het Van Goghmuseum rekent haar prenten „tot het mooiste wat op grafisch gebied in het fin de siècle is geproduceerd”. De drie aangekochte kleurenetsen – Het doorpassen, De brief en Badende vrouw – komen uit een serie van tien waarmee Cassatt haar naam als (prent)kunstenaar definitief vestigde. Ze maakte de etsen na een bezoek in 1890 aan een tentoonstelling van Japanse prenten in Parijs. Over die expositie schreef de Amerikaanse aan haar vriendin Berthe Morisot, een andere vrouwelijke impressionist: „We kunnen de Japanse prenten in de Beaux-Arts gaan bekijken. Echt, die mag je niet missen. Als je kleurenprenten wilt maken, is er niets mooiers voorstelbaar. Ik droom ervan en denk nergens anders meer aan dan aan kleur op koper."
- text: "Afgelopen zaterdagochtend werden Hunga Tonga en Hunga Hapai opnieuw twee aparte eilanden toen de vulkaan met een hevige explosie uitbarstte. De aanloop tot de uitbarsting begon al eind vorig jaar met kleinere explosies. Begin januari nam de activiteit af en dachten geologen dat de vulkaan tot rust was gekomen. Toch barstte hij afgelopen zaterdag opnieuw uit, veel heviger dan de uitbarstingen ervoor. Vlák voor deze explosie stortte het kilometerslange verbindingsstuk in en verdween onder het water. De eruptie duurde acht minuten. De wolk van as en giftige gasdeeltjes, zoals zwaveloxide, die daarbij vrijkwam, reikte tot dertig kilometer hoogte en was zo’n vijfhonderd kilometer breed. Ter vergelijking: de pluimen uit de recente vulkaanuitbarsting op La Palma reikten maximaal zo’n vijf kilometer hoog. De hoofdstad van Tonga, vijfenzestig kilometer verderop is bedekt met een dikke laag as. Dat heeft bijvoorbeeld gevolgen voor de veiligheid van het drinkwater op Tonga. De uitbarsting van de onderzeese vulkaan in de eilandstaat Tonga afgelopen zaterdag was bijzonder heftig. De eruptie veroorzaakte een tsunami die reikte van Nieuw-Zeeland tot de Verenigde Staten en in Nederland ging de luchtdruk omhoog. Geologen verwachten niet dat de vulkaan op Tonga voor een lange wereldwijde afkoeling zorgt, zoals bij andere hevige vulkaanuitbarstingen het geval is geweest. De vulkaan ligt onder water tussen de onbewoonde eilandjes Hunga Tonga (0,39 vierkante kilometer) en Hunga Ha’apai (0,65 vierkante kilometer). Magma dat bij kleinere uitbarsting in 2009 en 2014 omhoog kwam, koelde af en vormde een verbindingsstuk tussen de twee eilanden in. Een explosie van een onderwatervulkaan als die bij Tonga is heftiger dan bijvoorbeeld die uitbarsting op La Palma. „Dat komt doordat het vulkanisme hier veroorzaakt wordt door subductie: de Pacifische plaat zinkt onder Tonga de aardmantel in en neemt water mee omlaag”, zegt hoogleraar paleogeografie Douwe van Hinsbergen van de Universiteit Utrecht. „Dit water komt met magma als gas, als waterdamp, mee omhoog. Dat voert de druk onder de aardkost enorm op. Arwen Deuss, geowetenschapper aan de Universiteit Utrecht, vergelijkt het met een fles cola. „Wanneer je een fles cola schudt, zal het gas er met veel geweld uitkomen. Dat is waarschijnlijk wat er gebeurd is op Tonga, maar we weten het niet precies.”"
---

# T5 v1.1 Base finetuned for CNN news summarization in Dutch 🇳🇱

This model is [t5-v1.1-base-dutch-cased](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-cased) finetuned on [CNN Dailymail NL](https://huggingface.co/datasets/ml6team/cnn_dailymail_nl)

For a demo of the Dutch CNN summarization models, head over to the Hugging Face Spaces for
the **[Netherformer 📰](https://huggingface.co/spaces/flax-community/netherformer)** example application!

Rouge scores for this model are listed below.

## Tokenizer

* SentencePiece tokenizer trained from scratch for Dutch on mC4 nl cleaned with scripts from the Huggingface
  Transformers [Flax examples](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling).

## Dataset

All models listed below are trained on of the `full` configuration (39B tokens) of
[cleaned Dutch mC4](https://huggingface.co/datasets/yhavinga/mc4_nl_cleaned),
which is the original mC4, except

  * Documents that contained words from a selection of the Dutch and English [List of Dirty Naught Obscene and Otherwise Bad Words](https://github.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words) are removed
  * Sentences with less than 3 words are removed
  * Sentences with a word of more than 1000 characters are removed
  * Documents with less than 5 sentences are removed
  * Documents with "javascript", "lorum ipsum", "terms of use", "privacy policy", "cookie policy", "uses cookies",
    "use of cookies", "use cookies", "elementen ontbreken", "deze printversie" are removed.
 
## Models

TL;DR: [yhavinga/t5-v1.1-base-dutch-cased](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-cased) is the best model.

* `yhavinga/t5-base-dutch` is a re-training of the Dutch T5 base v1.0 model trained during the summer 2021
  Flax/Jax community week. Accuracy was improved from 0.64 to 0.70.
* The two T5 v1.1 base models are an uncased and cased version of `t5-v1.1-base`, again pre-trained from scratch on Dutch,
  with a tokenizer also trained from scratch. The t5 v1.1 models are slightly different from the t5 models, and the 
  base models are trained with a dropout of 0.0. For fine-tuning it is intended to set this back to 0.1.
* The large cased model is a pre-trained Dutch version of `t5-v1.1-large`. Training of t5-v1.1-large proved difficult. 
  Without dropout regularization, the training would diverge at a certain point. With dropout training went better,
  be it much slower than training the t5-model. At some point convergance was too slow to warrant further training.
  The latest checkpoint, training scripts and metrics are available for reference. For actual fine-tuning the cased
  base model is probably the better choice.

|                                                                                                   | model   | train seq len | acc      | loss     | batch size | epochs | steps   | dropout | optim     | lr   | duration |
|---------------------------------------------------------------------------------------------------|---------|---------------|----------|----------|------------|--------|---------|---------|-----------|------|----------|
| [yhavinga/t5-base-dutch](https://huggingface.co/yhavinga/t5-base-dutch)                           | T5      | 512           | 0,70     | 1,38     | 128        | 1      | 528481  | 0.1     | adafactor | 5e-3 | 2d 9h    |
| [yhavinga/t5-v1.1-base-dutch-uncased](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-uncased) | t5-v1.1 | 1024          | 0,73     | 1,20     | 64         | 2      | 1014525 | 0.0     | adafactor | 5e-3 | 5d 5h    |
| [yhavinga/t5-v1.1-base-dutch-cased](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-cased)     | t5-v1.1 | 1024          | **0,78** | **0,96** | 64         | 2      | 1210000 | 0.0     | adafactor | 5e-3 | 6d 6h    |
| [yhavinga/t5-v1.1-large-dutch-cased](https://huggingface.co/yhavinga/t5-v1.1-large-dutch-cased)   | t5-v1.1 | 512           | 0,76     | 1,07     | 64         | 1      | 1120000 | 0.1     | adafactor | 5e-3 | 86 13h   |

The cased t5-v1.1 Dutch models were fine-tuned on summarizing the CNN Daily Mail dataset.

|                                                                                                       | model   | input len | target len | Rouge1 | Rouge2 | RougeL | RougeLsum | Test Gen Len | epochs | batch size | steps | duration |
|-------------------------------------------------------------------------------------------------------|---------|-----------|------------|--------|--------|--------|-----------|--------------|--------|------------|-------|----------|
| [yhavinga/t5-v1.1-base-dutch-cnn-test](https://huggingface.co/yhavinga/t5-v1.1-base-dutch-cnn-test)   | t5-v1.1 | 1024      | 96         | 34,8   | 13,6   | 25,2   | 32,1      | 79           | 6      | 64         | 26916 | 2h 40m   |
| [yhavinga/t5-v1.1-large-dutch-cnn-test](https://huggingface.co/yhavinga/t5-v1.1-large-dutch-cnn-test) | t5-v1.1 | 1024      | 96         | 34,4   | 13,6   | 25,3   | 31,7      | 81           | 5      | 16         | 89720 | 11h      |


## Acknowledgements

This project would not have been possible without compute generously provided by Google through the
[TPU Research Cloud](https://sites.research.google/trc/). The HuggingFace 🤗 ecosystem was also
instrumental in many, if not all parts of the training. The following repositories where helpful in setting up the TPU-VM,
and training the models:

* [Gsarti's Pretrain and Fine-tune a T5 model with Flax on GCP](https://github.com/gsarti/t5-flax-gcp)
* [HUggingFace Flax MLM examples](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling)
* [Flax/Jax Community week t5-base-dutch](https://huggingface.co/flax-community/t5-base-dutch)

Created by [Yeb Havinga](https://www.linkedin.com/in/yeb-havinga-86530825/)