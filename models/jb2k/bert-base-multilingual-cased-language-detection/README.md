# bert-base-multilingual-cased-language-detection
A model for language detection with support for 45 languages
## Model description
This model was created by fine-tuning 
[bert-base-multilingual-cased](https://huggingface.co/bert-base-multilingual-cased) on the [common language](https://huggingface.co/datasets/common_language) dataset.
This dataset has support for 45 languages, which are listed below:
```
Arabic, Basque, Breton, Catalan, Chinese_China, Chinese_Hongkong, Chinese_Taiwan, Chuvash, Czech, Dhivehi, Dutch, English, Esperanto, Estonian, French, Frisian, Georgian, German, Greek, Hakha_Chin, Indonesian, Interlingua, Italian, Japanese, Kabyle, Kinyarwanda, Kyrgyz, Latvian, Maltese, Mongolian, Persian, Polish, Portuguese, Romanian, Romansh_Sursilvan, Russian, Sakha, Slovenian, Spanish, Swedish, Tamil, Tatar, Turkish, Ukranian, Welsh
```

## Evaluation
This model was evaluated on the test split of the [common language](https://huggingface.co/datasets/common_language) dataset, and achieved the following metrics:
* Accuracy: 97.8%
