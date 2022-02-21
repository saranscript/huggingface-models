---
license: mit
tags:
- generated_from_trainer
model-index:
- name: icebert-texas-squad-is
  results: []
widget:
- text: "Hvenær var Halldór Laxness í menntaskóla ?"
  context: "Halldór Laxness ( Halldór Kiljan ) fæddist í Reykjavík 23. apríl árið 1902 og átti í fyrstu heima við Laugaveg en árið 1905 settist fjölskyldan að í Laxnesi í Mosfellssveit . Þar ólst Halldór upp en sótti skóla í Reykjavík á unglingsárum . Ungur hélt hann síðan utan og var langdvölum erlendis um árabil – í ýmsum Evrópulöndum og síðar í Ameríku . Þegar hann var heima bjó hann í Reykjavík þar til hann og kona hans , Auður Sveinsdóttir , byggðu sér húsið Gljúfrastein í Mosfellssveit og fluttu þangað árið 1945 . Þar var heimili þeirra alla tíð síðan og þar er nú safn til minningar um þau . Halldór lést 8. febrúar 1998 . Skólaganga Halldórs varð ekki löng . Árið 1918 hóf hann nám við Menntaskólann í Reykjavík en hafði lítinn tíma til að læra , enda var hann að skrifa skáldsögu , Barn náttúrunnar , sem kom út haustið 1919 – þá þegar var höfundurinn ungi farinn af landi brott . Sagan vakti þó nokkra athygli og í Alþýðublaðinu sagði m.a. : „ Og hver veit nema að Halldór frá Laxnesi eigi eftir að verða óskabarn íslensku þjóðarinnar . “ Upp frá þessu sendi Halldór frá sér bók nánast á hverju ári , stundum fleiri en eina , í yfir sex áratugi . Afköst hans voru með eindæmum ; hann skrifaði fjölda skáldsagna , sumar í nokkrum hlutum , leikrit , kvæði , smásagnasöfn og endurminningabækur og gaf auk þess út mörg greinasöfn og ritgerðir . Bækurnar eru fjölbreyttar en eiga það sameiginlegt að vera skrifaðar af einstakri stílgáfu , djúpum mannskilningi og víðtækri þekkingu á sögu og samfélagi . Þar birtast oft afgerandi skoðanir á þjóðfélagsmálum og sögupersónur eru margar einkar eftirminnilegar ; tilsvör þeirra og lunderni hafa orðið samofin þjóðarsálinni . Þekktustu verk Halldórs eru eflaust skáldsögurnar stóru og rismiklu , s.s. Salka Valka , Sjálfstætt fólk , Heimsljós , Íslandsklukkan og Gerpla , og raunar mætti telja upp mun fleiri ; Kvæðabók hans er í uppáhaldi hjá mörgum sem og minningabækurnar sem hann skrifaði á efri árum um æskuár sín ; af þekktum greinasöfnum og ritgerðum má nefna Alþýðubókina og Skáldatíma . Mikið hefur verið skrifað um verk og ævi skáldsins , en hér skal aðeins bent á ítarlega frásögn og greiningu Halldórs Guðmundssonar í bókinni Halldór Laxness – ævisaga ."
---

# TExAS-SQuAD-is

This model is a fine-tuned version of [IceBERT](https://huggingface.co/vesteinn/IceBERT) on the TExAS-SQuAD-is dataset.
It achieves the following results on the evaluation set:
- Exact match: xx.xx%
- F1-score: xx.xx%

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
| 2.5353        | 0.12  | 500   | 2.2356          |
| 2.364         | 0.24  | 1000  | 2.0607          |
| 2.2243        | 0.36  | 1500  | 2.0617          |
| 2.1403        | 0.49  | 2000  | 1.9934          |
| 2.1491        | 0.61  | 2500  | 2.0515          |
| 2.0604        | 0.73  | 3000  | 1.9602          |
| 2.0232        | 0.85  | 3500  | 1.8954          |
| 2.0905        | 0.97  | 4000  | 1.9474          |
| 1.9229        | 1.09  | 4500  | 1.9814          |
| 1.9162        | 1.22  | 5000  | 1.9053          |
| 1.8937        | 1.34  | 5500  | 1.9501          |
| 1.9085        | 1.46  | 6000  | 1.8882          |
| 1.8671        | 1.58  | 6500  | 1.8996          |
| 1.8997        | 1.7   | 7000  | 1.8340          |
| 1.8546        | 1.82  | 7500  | 1.8883          |
| 1.8935        | 1.95  | 8000  | 1.8567          |
| 1.7031        | 2.07  | 8500  | 1.9206          |
| 1.7699        | 2.19  | 9000  | 1.8790          |
| 1.7016        | 2.31  | 9500  | 1.8670          |
| 1.7744        | 2.43  | 10000 | 1.8951          |
| 1.7518        | 2.55  | 10500 | 1.9550          |
| 1.7503        | 2.68  | 11000 | 1.9120          |
| 1.7818        | 2.8   | 11500 | 1.8820          |
| 1.6955        | 2.92  | 12000 | 1.8908          |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.8.1+cu101
- Datasets 1.12.1
- Tokenizers 0.10.3
