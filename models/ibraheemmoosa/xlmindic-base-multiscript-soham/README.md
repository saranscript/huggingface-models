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
- bh
- gom
- mai
license: apache-2.0
datasets:
- oscar
tags:
- multilingual
- albert
- fill-mask
- xlmindic
- nlp
- indoaryan
- indicnlp
- iso15919
- text-classification
widget:
- text : 'চীনের মধ্যাঞ্চলে আরও একটি শহরের বাসিন্দারা আবার ঘরবন্দী হয়ে পড়েছেন। আজ মঙ্গলবার নতুন করে লকডাউন–সংক্রান্ত বিধিনিষেধ জারি হওয়ার পর ঘরে আটকা পড়েছেন তাঁরা। করোনার অতি সংক্রামক নতুন ধরন অমিক্রনের বিস্তার ঠেকাতে এমন পদক্ষেপ নিয়েছে কর্তৃপক্ষ। খবর বার্তা সংস্থা এএফপির।'


co2_eq_emissions:
      emissions: "0.21 in grams of CO2"
      source: "calculated using this webstie https://mlco2.github.io/impact/#compute"
      training_type: "fine-tuning"
      geographical_location: "NA"
      hardware_used: "P100 for about 1.5 hours"
---

# XLMIndic Base Multiscript

This model is finetuned from [this model](https://huggingface.co/ibraheemmoosa/xlmindic-base-multiscript) on Soham Bangla News Classification task which is part of the IndicGLUE benchmark.

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

## Training procedure
### Preprocessing
The texts are  tokenized using SentencePiece and a vocabulary size of 50,000.

### Training
The model was trained for 8 epochs with a batch size of 16 and a learning rate of *2e-5*.
## Evaluation results

See results specific to Soham in the following table.
### IndicGLUE
Task | mBERT | XLM-R | IndicBERT-Base | XLMIndic-Base-Uniscript | XLMIndic-Base-Multiscript (This Model)
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
This model is pretrained on Indo-Aryan languages. Thus it is intended to be used for downstream tasks on these languages.
You can use the raw model for either masked language modeling or next sentence prediction, but it's mostly intended to
be fine-tuned on a downstream task. See the [model hub](https://huggingface.co/models?filter=xlmindic) to look for
fine-tuned versions on a task that interests you.
Note that this model is primarily aimed at being fine-tuned on tasks that use the whole sentence (potentially masked)
to make decisions, such as sequence classification, token classification or question answering. For tasks such as text
generation you should look at model like GPT2.

### How to use

Then you can use this model directly with a pipeline for masked language modeling:
```python
>>> from transformers import pipeline
>>> unmasker = pipeline('fill-mask', model='ibraheemmoosa/xlmindic-base-multiscript')
>>> text = "রবীন্দ্রনাথ ঠাকুর এফআরএএস (৭ মে ১৮৬১ - ৭ আগস্ট ১৯৪১; ২৫ বৈশাখ ১২৬৮ - ২২ শ্রাবণ ১৩৪৮ বঙ্গাব্দ) ছিলেন অগ্রণী বাঙালি [MASK], ঔপন্যাসিক, সংগীতস্রষ্টা, নাট্যকার, চিত্রকর, ছোটগল্পকার, প্রাবন্ধিক, অভিনেতা, কণ্ঠশিল্পী ও দার্শনিক। ১৯১৩ সালে গীতাঞ্জলি কাব্যগ্রন্থের ইংরেজি অনুবাদের জন্য তিনি এশীয়দের মধ্যে সাহিত্যে প্রথম নোবেল পুরস্কার লাভ করেন।"
>>> unmasker(text)
[{'score': 0.34163928031921387,
  'token': 5399,
  'token_str': 'কবি',
  'sequence': 'রবীন্দ্রনাথ ঠাকুর এফআরএএস (৭ মে ১৮৬১ - ৭ আগস্ট ১৯৪১; ২৫ বৈশাখ ১২৬৮ - ২২ শ্রাবণ ১৩৪৮ বঙ্গাব্দ) ছিলেন অগ্রণী বাঙালি কবি, পন্যাসিক, সংগীতস্রষ্টা, নাট্যকার, চিত্রকর, ছোটগল্পকার, প্রাবন্ধিক, অভিনেতা, কণ্ঠশিল্পী ও দার্শনিক। ১৯১৩ সালে গীতাঞ্জলি কাব্যগ্রন্থের ইংরেজি অনুবাদের জন্য তিনি এশীয়দের মধ্যে সাহিত্যে প্রথম নোবেল পুরস্কার লাভ করেন।'},
 {'score': 0.30519795417785645,
  'token': 33436,
  'token_str': 'people',
  'sequence': 'রবীন্দ্রনাথ ঠাকুর এফআরএএস (৭ মে ১৮৬১ - ৭ আগস্ট ১৯৪১; ২৫ বৈশাখ ১২৬৮ - ২২ শ্রাবণ ১৩৪৮ বঙ্গাব্দ) ছিলেন অগ্রণী বাঙালি people, পন্যাসিক, সংগীতস্রষ্টা, নাট্যকার, চিত্রকর, ছোটগল্পকার, প্রাবন্ধিক, অভিনেতা, কণ্ঠশিল্পী ও দার্শনিক। ১৯১৩ সালে গীতাঞ্জলি কাব্যগ্রন্থের ইংরেজি অনুবাদের জন্য তিনি এশীয়দের মধ্যে সাহিত্যে প্রথম নোবেল পুরস্কার লাভ করেন।'},
 {'score': 0.29130080342292786,
  'token': 30476,
  'token_str': 'সাহিত্যিক',
  'sequence': 'রবীন্দ্রনাথ ঠাকুর এফআরএএস (৭ মে ১৮৬১ - ৭ আগস্ট ১৯৪১; ২৫ বৈশাখ ১২৬৮ - ২২ শ্রাবণ ১৩৪৮ বঙ্গাব্দ) ছিলেন অগ্রণী বাঙালি সাহিত্যিক, পন্যাসিক, সংগীতস্রষ্টা, নাট্যকার, চিত্রকর, ছোটগল্পকার, প্রাবন্ধিক, অভিনেতা, কণ্ঠশিল্পী ও দার্শনিক। ১৯১৩ সালে গীতাঞ্জলি কাব্যগ্রন্থের ইংরেজি অনুবাদের জন্য তিনি এশীয়দের মধ্যে সাহিত্যে প্রথম নোবেল পুরস্কার লাভ করেন।'},
 {'score': 0.031051287427544594,
  'token': 6139,
  'token_str': 'লেখক',
  'sequence': 'রবীন্দ্রনাথ ঠাকুর এফআরএএস (৭ মে ১৮৬১ - ৭ আগস্ট ১৯৪১; ২৫ বৈশাখ ১২৬৮ - ২২ শ্রাবণ ১৩৪৮ বঙ্গাব্দ) ছিলেন অগ্রণী বাঙালি লেখক, পন্যাসিক, সংগীতস্রষ্টা, নাট্যকার, চিত্রকর, ছোটগল্পকার, প্রাবন্ধিক, অভিনেতা, কণ্ঠশিল্পী ও দার্শনিক। ১৯১৩ সালে গীতাঞ্জলি কাব্যগ্রন্থের ইংরেজি অনুবাদের জন্য তিনি এশীয়দের মধ্যে সাহিত্যে প্রথম নোবেল পুরস্কার লাভ করেন।'},
 {'score': 0.002705035964027047,
  'token': 38443,
  'token_str': 'শিল্পীরা',
  'sequence': 'রবীন্দ্রনাথ ঠাকুর এফআরএএস (৭ মে ১৮৬১ - ৭ আগস্ট ১৯৪১; ২৫ বৈশাখ ১২৬৮ - ২২ শ্রাবণ ১৩৪৮ বঙ্গাব্দ) ছিলেন অগ্রণী বাঙালি শিল্পীরা, পন্যাসিক, সংগীতস্রষ্টা, নাট্যকার, চিত্রকর, ছোটগল্পকার, প্রাবন্ধিক, অভিনেতা, কণ্ঠশিল্পী ও দার্শনিক। ১৯১৩ সালে গীতাঞ্জলি কাব্যগ্রন্থের ইংরেজি অনুবাদের জন্য তিনি এশীয়দের মধ্যে সাহিত্যে প্রথম নোবেল পুরস্কার লাভ করেন।'}]
```
### Limitations and bias
Even though we pretrain on a comparatively large multilingual corpus the model may exhibit harmful gender, ethnic and political bias. If you fine-tune this model on a task where these issues are important you should take special care when relying on the model to make decisions.

## Contact
Feel free to contact us if you have any ideas or if you want to know more about our models.
- Ibraheem Muhammad Moosa (ibraheemmoosa1347@gmail.com)
- Mahmud Elahi Akhter (mahmud.akhter01@northsouth.edu)
- Ashfia Binte Habib

## BibTeX entry and citation info

```bibtex
@article{Moosa2022DoesTH,
  title={Does Transliteration Help Multilingual Language Modeling?},
  author={Ibraheem Muhammad Moosa and Mahmuda Akhter and Ashfia Binte Habib},
  journal={ArXiv},
  year={2022},
  volume={abs/2201.12501}
}
```