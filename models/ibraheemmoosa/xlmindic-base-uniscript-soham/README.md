---
language:
- as
- bn
- gu
- hi
- mr
- ne
- or
- pa
- si
- sa
- bpy
- mai
- bh
- gom
license: apache-2.0
datasets:
- oscar
tags:
- multilingual
- albert
- xlmindic
- nlp
- indoaryan
- indicnlp
- iso15919
- transliteration
- text-classification
widget:
- text : 'cīnēra madhyāñcalē āraō ēkaṭi śaharēra bāsindārā ābāra gharabandī haẏē paṛēchēna. āja maṅgalabāra natuna karē lakaḍāuna–saṁkrānta bidhiniṣēdha jāri haōẏāra para gharē āṭakā paṛēchēna tām̐rā. karōnāra ati saṁkrāmaka natuna dharana amikranēra bistāra ṭhēkātē ēmana padakṣēpa niẏēchē kartr̥pakṣa. khabara bārtā saṁsthā ēēphapira.'

co2_eq_emissions:
      emissions: "0.21 in grams of CO2"
      source: "calculated using this webstie https://mlco2.github.io/impact/#compute"
      training_type: "fine-tuning"
      geographical_location: "NA"
      hardware_used: "P100 for about 1.5 hours"
---

# XLMIndic Base Uniscript

This model is finetuned from [this model](https://huggingface.co/ibraheemmoosa/xlmindic-base-uniscript) on Soham Bangla News Classification task which is part of the IndicGLUE benchmark. **Before pretraining this model we transliterate the text to [ISO-15919](https://en.wikipedia.org/wiki/ISO_15919) format using the [Aksharamukha](https://pypi.org/project/aksharamukha/)
library.** A demo of Aksharamukha library is hosted [here](https://aksharamukha.appspot.com/converter)
where you can transliterate your text and use it on our model on the inference widget.

## Model description

This model has the same configuration as the [ALBERT Base v2 model](https://huggingface.co/albert-base-v2/). Specifically, this model has the following configuration:

- 12 repeating layers
- 128 embedding dimension
- 768 hidden dimension
- 12 attention heads
- 11M parameters
- 512 sequence length

## Training data
This model was fine-tuned on Soham dataset that is part of the IndicGLUE benchmark.

## Transliteration

*The unique component of this model is that it takes in ISO-15919 transliterated text.*

The motivation behind this is this. When two languages share vocabularies, a machine learning model can exploit that to learn good cross-lingual representations. However if these two languages use different writing scripts it is difficult for a model to make the connection. Thus if if we can write the two languages in a single script then it is easier for the model to learn good cross-lingual representation.

For many of the scripts currently in use, there are standard transliteration schemes to convert to the Latin script. In particular, for the Indic scripts the ISO-15919 transliteration scheme is designed to consistently transliterate texts written in different Indic scripts to the Latin script.

An example of ISO-15919 transliteration for a piece of **Bangla** text is the following:

**Original:** "রবীন্দ্রনাথ ঠাকুর এফআরএএস (৭ মে ১৮৬১ - ৭ আগস্ট ১৯৪১; ২৫ বৈশাখ ১২৬৮ - ২২ শ্রাবণ ১৩৪৮ বঙ্গাব্দ) ছিলেন অগ্রণী বাঙালি কবি, ঔপন্যাসিক, সংগীতস্রষ্টা, নাট্যকার, চিত্রকর, ছোটগল্পকার, প্রাবন্ধিক, অভিনেতা, কণ্ঠশিল্পী ও দার্শনিক।"

**Transliterated:** 'rabīndranātha ṭhākura ēphaāraēēsa (7 mē 1861 - 7 āgasṭa 1941; 25 baiśākha 1268 - 22 śrābaṇa 1348 baṅgābda) chilēna agraṇī bāṅāli kabi, aupanyāsika, saṁgītasraṣṭā, nāṭyakāra, citrakara, chōṭagalpakāra, prābandhika, abhinētā, kaṇṭhaśilpī ō dārśanika.'

Another example for a piece of **Hindi** text is the following:

**Original:** "चूंकि मानव परिवार के सभी सदस्यों के जन्मजात गौरव और समान तथा अविच्छिन्न अधिकार की स्वीकृति ही विश्व-शान्ति, न्याय और स्वतन्त्रता की बुनियाद है"

**Transliterated:** "cūṁki mānava parivāra kē sabhī sadasyōṁ kē janmajāta gaurava aura samāna tathā avicchinna adhikāra kī svīkr̥ti hī viśva-śānti, nyāya aura svatantratā kī buniyāda hai"
 
 
## Training procedure

### Preprocessing

The texts are transliterated to ISO-15919 format using the Aksharamukha library. Then these are tokenized using SentencePiece and a vocabulary size of 50,000.

### Training

The model was trained for 8 epochs with a batch size of 16 and a learning rate of *2e-5*.

## Evaluation results
See results specific to Soham in the following table.

### IndicGLUE
Task | mBERT | XLM-R | IndicBERT-Base | XLMIndic-Base-Uniscript (This Model) | XLMIndic-Base-Multiscript (Ablation Model)
-----| ----- | ----- | ------ | ------- | --------
Wikipedia Section Title Prediction | 71.90 | 65.45 | 69.40 | **81.78 ± 0.60** | 77.17 ± 0.76
Article Genre Classification | 88.64 | 96.61 | 97.72 | **98.70 ± 0.29** | 98.30 ± 0.26
Named Entity Recognition (F1-score) | 71.29 | 62.18 | 56.69 | **89.85 ± 1.14** |  83.19 ± 1.58
BBC Hindi News Article Classification | 60.55 | 75.52 | 74.60 | **79.14 ± 0.60** | 77.28 ± 1.50
Soham Bangla News Article Classification | 80.23 | 87.6 | 78.45 | **93.89 ± 0.48** | 93.22 ± 0.49
INLTK Gujarati Headlines Genre Classification | - | - | **92.91** | 90.73 ± 0.75 | 90.41 ± 0.69
INLTK Marathi Headlines Genre Classification | - | - | **94.30** | 92.04 ± 0.47 | 92.21 ± 0.23
IITP Hindi Product Reviews Sentiment Classification | 74.57 | **78.97** | 71.32 | 77.18 ± 0.77 | 76.33 ± 0.84
IITP Hindi Movie Reviews Sentiment Classification | 56.77 | 61.61 | 59.03 | **66.34 ± 0.16** | 65.91 ± 2.20
MIDAS Hindi Discourse Type Classification | 71.20 | **79.94** | 78.44 | 78.54 ± 0.91 | 78.39 ± 0.33
Cloze Style Question Answering (Fill-mask task) | - | - | 37.16 | **41.54** | 38.21

## Intended uses & limitations

This model is pretrained on Indo-Aryan languages. Thus it is intended to be used for downstream tasks on these languages. However, since Dravidian languages such as Malayalam, Telegu, Kannada etc share a lot of vocabulary with the Indo-Aryan languages, this model can potentially be used on those languages too (after transliterating the text to ISO-15919).

You can use the raw model for either masked language modeling or next sentence prediction, but it's mostly intended to
be fine-tuned on a downstream task. See the [model hub](https://huggingface.co/models?filter=xlmindic) to look for
fine-tuned versions on a task that interests you.
Note that this model is primarily aimed at being fine-tuned on tasks that use the whole sentence (potentially masked)
to make decisions, such as sequence classification, token classification or question answering. For tasks such as text
generation you should look at model like GPT2.

### How to use

To use this model you will need to first install the [Aksharamukha](https://pypi.org/project/aksharamukha/) library.

```bash
pip install aksharamukha
```

Using this library you can transliterate any text wriiten in Indic scripts in the following way:
```python
>>> from aksharamukha import transliterate
>>> text = "चूंकि मानव परिवार के सभी सदस्यों के जन्मजात गौरव और समान तथा अविच्छिन्न अधिकार की स्वीकृति ही विश्व-शान्ति, न्याय और स्वतन्त्रता की बुनियाद है"
>>> transliterated_text = transliterate.process('autodetect', 'ISO', text)
>>> transliterated_text
"cūṁki mānava parivāra kē sabhī sadasyōṁ kē janmajāta gaurava aura samāna tathā avicchinna adhikāra kī svīkr̥ti hī viśva-śānti, nyāya aura svatantratā kī buniyāda hai"
```

Then you can use this model directly with a pipeline for masked language modeling:

```python
>>> from transformers import pipeline
>>> from aksharamukha import transliterate
>>> unmasker = pipeline('fill-mask', model='ibraheemmoosa/xlmindic-base-uniscript')
>>> text = "রবীন্দ্রনাথ ঠাকুর এফআরএএস (৭ মে ১৮৬১ - ৭ আগস্ট ১৯৪১; ২৫ বৈশাখ ১২৬৮ - ২২ শ্রাবণ ১৩৪৮ বঙ্গাব্দ) ছিলেন অগ্রণী বাঙালি [MASK], ঔপন্যাসিক, সংগীতস্রষ্টা, নাট্যকার, চিত্রকর, ছোটগল্পকার, প্রাবন্ধিক, অভিনেতা, কণ্ঠশিল্পী ও দার্শনিক। ১৯১৩ সালে গীতাঞ্জলি কাব্যগ্রন্থের ইংরেজি অনুবাদের জন্য তিনি এশীয়দের মধ্যে সাহিত্যে প্রথম নোবেল পুরস্কার লাভ করেন।"
>>> transliterated_text = transliterate.process('Bengali', 'ISO', text)
>>> transliterated_text
'rabīndranātha ṭhākura ēphaāraēēsa (7 mē 1861 - 7 āgasṭa 1941; 25 baiśākha 1268 - 22 śrābaṇa 1348 baṅgābda) chilēna agraṇī bāṅāli [MASK], aupanyāsika, saṁgītasraṣṭā, nāṭyakāra, citrakara, chōṭagalpakāra, prābandhika, abhinētā, kaṇṭhaśilpī ō dārśanika. 1913 sālē gītāñjali kābyagranthēra iṁrēji anubādēra janya tini ēśīẏadēra madhyē sāhityē prathama [MASK] puraskāra lābha karēna.'
>>> unmasker(transliterated_text)
[{'score': 0.39705055952072144,
  'token': 1500,
  'token_str': 'abhinētā',
  'sequence': 'rabīndranātha ṭhākura ēphaāraēēsa (7 mē 1861 - 7 āgasṭa 1941; 25 baiśākha 1268 - 22 śrābaṇa 1348 baṅgābda) chilēna agraṇī bāṅāli abhinētā, aupanyāsika, saṁgītasraṣṭā, nāṭyakāra, citrakara, chōṭagalpakāra, prābandhika, abhinētā, kaṇṭhaśilpī ō dārśanika. 1913 sālē gītāñjali kābyagranthēra iṁrēji anubādēra janya tini ēśīẏadēra madhyē sāhityē prathama nōbēla puraskāra lābha karēna.'},
 {'score': 0.20499080419540405,
  'token': 3585,
  'token_str': 'kabi',
  'sequence': 'rabīndranātha ṭhākura ēphaāraēēsa (7 mē 1861 - 7 āgasṭa 1941; 25 baiśākha 1268 - 22 śrābaṇa 1348 baṅgābda) chilēna agraṇī bāṅāli kabi, aupanyāsika, saṁgītasraṣṭā, nāṭyakāra, citrakara, chōṭagalpakāra, prābandhika, abhinētā, kaṇṭhaśilpī ō dārśanika. 1913 sālē gītāñjali kābyagranthēra iṁrēji anubādēra janya tini ēśīẏadēra madhyē sāhityē prathama nōbēla puraskāra lābha karēna.'},
 {'score': 0.1314290314912796,
  'token': 15402,
  'token_str': 'rājanētā',
  'sequence': 'rabīndranātha ṭhākura ēphaāraēēsa (7 mē 1861 - 7 āgasṭa 1941; 25 baiśākha 1268 - 22 śrābaṇa 1348 baṅgābda) chilēna agraṇī bāṅāli rājanētā, aupanyāsika, saṁgītasraṣṭā, nāṭyakāra, citrakara, chōṭagalpakāra, prābandhika, abhinētā, kaṇṭhaśilpī ō dārśanika. 1913 sālē gītāñjali kābyagranthēra iṁrēji anubādēra janya tini ēśīẏadēra madhyē sāhityē prathama nōbēla puraskāra lābha karēna.'},
 {'score': 0.060830358415842056,
  'token': 3212,
  'token_str': 'kalākāra',
  'sequence': 'rabīndranātha ṭhākura ēphaāraēēsa (7 mē 1861 - 7 āgasṭa 1941; 25 baiśākha 1268 - 22 śrābaṇa 1348 baṅgābda) chilēna agraṇī bāṅāli kalākāra, aupanyāsika, saṁgītasraṣṭā, nāṭyakāra, citrakara, chōṭagalpakāra, prābandhika, abhinētā, kaṇṭhaśilpī ō dārśanika. 1913 sālē gītāñjali kābyagranthēra iṁrēji anubādēra janya tini ēśīẏadēra madhyē sāhityē prathama nōbēla puraskāra lābha karēna.'},
 {'score': 0.035522934049367905,
  'token': 11586,
  'token_str': 'sāhityakāra',
  'sequence': 'rabīndranātha ṭhākura ēphaāraēēsa (7 mē 1861 - 7 āgasṭa 1941; 25 baiśākha 1268 - 22 śrābaṇa 1348 baṅgābda) chilēna agraṇī bāṅāli sāhityakāra, aupanyāsika, saṁgītasraṣṭā, nāṭyakāra, citrakara, chōṭagalpakāra, prābandhika, abhinētā, kaṇṭhaśilpī ō dārśanika. 1913 sālē gītāñjali kābyagranthēra iṁrēji anubādēra janya tini ēśīẏadēra madhyē sāhityē prathama nōbēla puraskāra lābha karēna.'}]
```

### Limitations and bias

Even though we pretrain on a comparatively large multilingual corpus the model may exhibit harmful gender, ethnic and political bias. If you fine-tune this model on a task where these issues are important you should take special care when relying on the model to make decisions.

## Contact

Feel free to contact us if you have any ideas or if you want to know more about our models.
- Ibraheem Muhammad Moosa (ibraheemmoosa1347@gmail.com)
- Mahmud Elahi Akhter (mahmud.akhter01@northsouth.edu)
- Ashfia Binte Habib

## BibTeX entry and citation info

Coming soon!
