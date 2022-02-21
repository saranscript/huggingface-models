---
license: mit
tags:
- generated_from_trainer
model-index:
- name: xlmr-base-texas-squad-is
  results: []
widget:
- text: "Hvenær var Halldór Laxness í menntaskóla ?"
  context: "Halldór Laxness ( Halldór Kiljan ) fæddist í Reykjavík 23. apríl árið 1902 og átti í fyrstu heima við Laugaveg en árið 1905 settist fjölskyldan að í Laxnesi í Mosfellssveit . Þar ólst Halldór upp en sótti skóla í Reykjavík á unglingsárum . Ungur hélt hann síðan utan og var langdvölum erlendis um árabil – í ýmsum Evrópulöndum og síðar í Ameríku . Þegar hann var heima bjó hann í Reykjavík þar til hann og kona hans , Auður Sveinsdóttir , byggðu sér húsið Gljúfrastein í Mosfellssveit og fluttu þangað árið 1945 . Þar var heimili þeirra alla tíð síðan og þar er nú safn til minningar um þau . Halldór lést 8. febrúar 1998 . Skólaganga Halldórs varð ekki löng . Árið 1918 hóf hann nám við Menntaskólann í Reykjavík en hafði lítinn tíma til að læra , enda var hann að skrifa skáldsögu , Barn náttúrunnar , sem kom út haustið 1919 – þá þegar var höfundurinn ungi farinn af landi brott . Sagan vakti þó nokkra athygli og í Alþýðublaðinu sagði m.a. : „ Og hver veit nema að Halldór frá Laxnesi eigi eftir að verða óskabarn íslensku þjóðarinnar . “ Upp frá þessu sendi Halldór frá sér bók nánast á hverju ári , stundum fleiri en eina , í yfir sex áratugi . Afköst hans voru með eindæmum ; hann skrifaði fjölda skáldsagna , sumar í nokkrum hlutum , leikrit , kvæði , smásagnasöfn og endurminningabækur og gaf auk þess út mörg greinasöfn og ritgerðir . Bækurnar eru fjölbreyttar en eiga það sameiginlegt að vera skrifaðar af einstakri stílgáfu , djúpum mannskilningi og víðtækri þekkingu á sögu og samfélagi . Þar birtast oft afgerandi skoðanir á þjóðfélagsmálum og sögupersónur eru margar einkar eftirminnilegar ; tilsvör þeirra og lunderni hafa orðið samofin þjóðarsálinni . Þekktustu verk Halldórs eru eflaust skáldsögurnar stóru og rismiklu , s.s. Salka Valka , Sjálfstætt fólk , Heimsljós , Íslandsklukkan og Gerpla , og raunar mætti telja upp mun fleiri ; Kvæðabók hans er í uppáhaldi hjá mörgum sem og minningabækurnar sem hann skrifaði á efri árum um æskuár sín ; af þekktum greinasöfnum og ritgerðum má nefna Alþýðubókina og Skáldatíma . Mikið hefur verið skrifað um verk og ævi skáldsins , en hér skal aðeins bent á ítarlega frásögn og greiningu Halldórs Guðmundssonar í bókinni Halldór Laxness – ævisaga ."
---

# TExAS-SQuAD-is

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on the TExAS-SQuAD-is dataset.
It achieves the following results on the evaluation set:
- Exact match: 56.91%
- F1-score: 59.93%

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
| 2.1458        | 1.0   | 4219  | 1.8892          |
| 1.9202        | 2.0   | 8438  | 1.8566          |
| 1.7377        | 3.0   | 12657 | 1.8688          |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.8.1+cu101
- Datasets 1.12.1
- Tokenizers 0.10.3
