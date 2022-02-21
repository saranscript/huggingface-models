---
language: 
- dutch
tags:
- summarization
- seq2seq
- text-generation
datasets:
- cnn_dailymail
- xsum
pipeline_tag: text2text-generation
widget:
- text: "Onderzoekers ontdekten dat vier van de vijf kinderen in Engeland die op school lunches hadden gegeten, op school voedsel hadden geprobeerd dat ze thuis niet hadden geprobeerd.De helft van de ondervraagde ouders zei dat hun kinderen hadden gevraagd om voedsel dat ze op school hadden gegeten om thuis te worden gekookt.De enquête, van ongeveer 1.000 ouders, vond dat de meest populaire groenten wortelen, suikermaïs en erwten waren.Aubergine, kikkererwten en spinazie waren een van de minst populaire.Van de ondervraagde ouders, 628 hadden kinderen die lunches op school aten. (% duidt op een deel van de ouders die zeiden dat hun kind elke groente zou eten) England's School Food Trust gaf opdracht tot het onderzoek na een onderzoek door de Mumsnet-website suggereerde dat sommige ouders hun kinderen lunchpakket gaven omdat ze dachten dat ze te kieskeurig waren om iets anders te eten. \"Schoolmaaltijden kunnen een geweldige manier zijn om ouders te helpen hun kinderen aan te moedigen om nieuw voedsel te proberen en om de verscheidenheid van voedsel in hun dieet te verhogen. \"Mumsnet medeoprichter, Carrie Longton, zei: \"Het krijgen van kinderen om gezond te eten is de droom van elke ouder, maar maaltijdtijden thuis kan vaak een slagveld en emotioneel geladen zijn. \"Vanuit Mumsnetters' ervaring lijkt het erop dat eenmaal op school is er een verlangen om in te passen bij iedereen anders en zelfs een aantal positieve peer pressure om op te scheppen over de verscheidenheid van wat voedsel je kunt eten. \"Schoolmaaltijden zijn ook verplaatst op nogal een beetje van toen Mumsnetters op school waren, met gezondere opties en meer afwisseling. \"Schoolmaaltijden in Engeland moeten nu voldoen aan strenge voedingsrichtlijnen.Ongeveer vier op de tien basisschoolkinderen in Engeland eten nu schoollunches, iets meer dan op middelbare scholen.Meer kinderen in Schotland eten schoollunches - ongeveer 46%.Het onderzoek werd online uitgevoerd tussen 26 februari en 5 maart onder een panel van ouders die ten minste één kind op school hadden van 4-17 jaar oud."
- text: "Het Londense trio staat klaar voor de beste Britse act en beste album, evenals voor twee nominaties in de beste song categorie. \"We kregen te horen zoals vanmorgen 'Oh I think you're genomineerd',\" zei Dappy. \"En ik was als 'Oh yeah, what one?' En nu zijn we genomineerd voor vier awards. Ik bedoel, wow! \"Bandmate Fazer voegde eraan toe: \"We dachten dat het het beste van ons was om met iedereen naar beneden te komen en hallo te zeggen tegen de camera's.En nu vinden we dat we vier nominaties hebben. \"De band heeft twee shots bij de beste song prijs, het krijgen van het knikje voor hun Tyncy Stryder samenwerking nummer één, en single Strong Again.Their album Uncle B zal ook gaan tegen platen van Beyonce en Kany \"Aan het eind van de dag zijn we dankbaar om te zijn waar we zijn in onze carrières. \"Als het niet gebeurt dan gebeurt het niet - live om te vechten een andere dag en blijven maken albums en hits voor de fans. \"Dappy onthulde ook dat ze kunnen worden optreden live op de avond.De groep zal doen Nummer Een en ook een mogelijke uitlevering van de War Child single, I Got Soul.Het liefdadigheidslied is een re-working van The Killers' All These Things That I've Done en is ingesteld op artiesten als Chipmunk, Ironik en Pixie Lott.Dit jaar zal Mobos worden gehouden buiten Londen voor de eerste keer, in Glasgow op 30 september.N-Dubz zei dat ze op zoek waren naar optredens voor hun Schotse fans en bogen over hun recente shows ten noorden van de Londense We hebben Aberdeen ongeveer drie of vier maanden geleden gedaan - we hebben die show daar verbrijzeld! Overal waar we heen gaan slaan we hem in elkaar!\""
---

# t5-base-dutch-demo 📰

Created by [Yeb Havinga](https://www.linkedin.com/in/yeb-havinga-86530825/) & [Dat Nguyen](https://www.linkedin.com/in/dat-nguyen-49a641138/) during the [Hugging Face community week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104)

This model is based on [t5-base-dutch](https://huggingface.co/flax-community/t5-base-dutch) 
and fine-tuned to create summaries of news articles.

For a demo of the model, head over to the Hugging Face Spaces for the **[Netherformer 📰](https://huggingface.co/spaces/flax-community/netherformer)** example application!

## Dataset


`t5-base-dutch-demo` is fine-tuned on three mixed news sources:

 1. **CNN DailyMail** translated to Dutch with MarianMT.
 2. **XSUM** translated to Dutch with MarianMt.
 3. News article summaries distilled from the nu.nl website.

The total number of training examples in this dataset is 1366592.
 
## Training

Training consisted of fine-tuning [t5-base-dutch](https://huggingface.co/flax-community/t5-base-dutch) with
the following parameters:

 * Constant learning rate 0.0005
 * Batch size 8
 * 1 epoch (170842 steps)

## Evaluation

The performance of the summarization model is measured with the Rouge metric from the
Huggingface Datasets library.

```
    "rouge{n}" (e.g. `"rouge1"`, `"rouge2"`) where: {n} is the n-gram based scoring,
    "rougeL": Longest common subsequence based scoring.
```

 * Rouge1: 23.8
 * Rouge2: 6.9
 * RougeL: 19.7

These scores are expected to improve if the model is trained with evaluation configured
for the CNN DM and XSUM datasets (translated to Dutch) individually.