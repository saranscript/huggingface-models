---
language: english
thumbnail: https://github.githubassets.com/images/icons/emoji/unicode/2695.png
widget:
- text: "Lung infiltrates cause significant morbidity and mortality in immunocompromised <mask>."
- text: "Tuberculosis appears to be an important <mask> in endemic regions especially in the non-HIV, non-hematologic malignancy group."
- text: "For vector-transmitted diseases this places huge significance on vector mortality rates as vectors usually don't <mask> an infection and instead remain infectious for life."
- text: "The lung lesions were characterized by bronchointerstitial pneumonia with accumulation of neutrophils, macrophages and necrotic debris in <mask> and bronchiolar lumens and peribronchiolar/perivascular infiltration of inflammatory cells."
---

# roberta-cord19-1M7k

![](https://github.githubassets.com/images/icons/emoji/unicode/2695.png)

> This model is based on ***RoBERTa*** and was pre-trained on 1.7 million sentences.

The training corpus was papers taken from *Semantic Scholar*'s CORD-19 historical releases. Corpus size is `13k` papers, `~60M` tokens. I used the full-text `"body_text"` of the papers in training (details below).

#### Usage

```python
from transformers import pipeline
from transformers import RobertaTokenizerFast, RobertaForMaskedLM

tokenizer = RobertaTokenizerFast.from_pretrained("amoux/roberta-cord19-1M7k")
model = RobertaForMaskedLM.from_pretrained("amoux/roberta-cord19-1M7k")

fillmask = pipeline("fill-mask", model=model, tokenizer=tokenizer)

text = "Lung infiltrates cause significant morbidity and mortality in immunocompromised patients."
masked_text = text.replace("patients", tokenizer.mask_token)
predictions = fillmask(masked_text, top_k=3)
```

- Predicted tokens

```bash
[{'sequence': '<s>Lung infiltrates cause significant morbidity and mortality in immunocompromised patients.</s>',
  'score': 0.6273621320724487,
  'token': 660,
  'token_str': 'Ġpatients'},
 {'sequence': '<s>Lung infiltrates cause significant morbidity and mortality in immunocompromised individuals.</s>',
  'score': 0.19800445437431335,
  'token': 1868,
  'token_str': 'Ġindividuals'},
 {'sequence': '<s>Lung infiltrates cause significant morbidity and mortality in immunocompromised animals.</s>',
  'score': 0.022069649770855904,
  'token': 1471,
  'token_str': 'Ġanimals'}]
```

## Dataset

- About
	- name: *CORD-19: The Covid-19 Open Research Dataset*
	- date: *2020-03-18*
	- md5 | sha1: `a36fe181 | 8fbea927`
	- text-key: `body_text`
	- subsets (*total*: `13,202`):
	    - *biorxiv_medrxiv*: `803`
	    - *comm_use_subset*: `9000`
	    - *pmc_custom_license*: `1426`
	    - *noncomm_use_subset*: `1973`
- Splits (*ratio: 0.9*)
	- sentences used for training: `1,687,124`
	- sentences used for evaluation: `187,459`
- Total training steps: `210,890`
- Total evaluation steps: `23,433`

## Parameters

- Data
	- block_size: `256`
- Training
	- per_device_train_batch_size: `8`
	- per_device_eval_batch_size: `8`
	- gradient_accumulation_steps: `2`
	- learning_rate: `5e-5`
	- num_train_epochs: `2`
	- fp16: `True`
	- fp16_opt_level: `'01'`
	- seed: `42`
- Output
    - global_step: `210890`
    - training_loss: `3.5964575726682155`

## Evaluation

- Perplexity: `17.469366079957922`

### Citation

> Allen Institute CORD-19 [Historical Releases](https://ai2-semanticscholar-cord-19.s3-us-west-2.amazonaws.com/historical_releases.html)

```
@article{Wang2020CORD19TC,
	title={CORD-19: The Covid-19 Open Research Dataset},
	author={Lucy Lu Wang and Kyle Lo and Yoganand Chandrasekhar and Russell Reas and Jiangjiang Yang and Darrin Eide and K. Funk and Rodney Michael Kinney and Ziyang Liu and W. Merrill and P. Mooney and D. Murdick and Devvret Rishi and Jerry Sheehan and Zhihong Shen and B. Stilson and A. Wade and K. Wang and Christopher Wilhelm and Boya Xie and D. Raymond and Daniel S. Weld and Oren Etzioni and Sebastian Kohlmeier},
	journal={ArXiv},
	year={2020}
}
```