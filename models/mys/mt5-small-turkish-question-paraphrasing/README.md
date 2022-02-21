## Overview
This model is a finetuned version of [mt5-small](https://huggingface.co/google/mt5-small) for question paraphrasing task in Turkish. As a generator model, its capabilities are currently investigated and there is an ongoing effort to further improve it. You can raise an issue [in this GitHub repo](https://github.com/monatis/tqp) for any comments, suggestions or interesting findings when using this model.

## Usage
You can generate 5 paraphrases for the input question with The simple code below.

```python
from transformers import AutoTokenizer, T5ForConditionalGeneration
model_name = "mys/mt5-small-turkish-question-paraphrasing"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = T5ForConditionalGeneration.from_pretrained(model_name)

tokens = tokenizer.encode_plus("Yarın toplantı kaçta başlıyor?", return_tensors='pt')
paraphrases = model.generate(tokens['input_ids'], max_length=128, num_return_sequences=5, num_beams=5)
tokenizer.batch_decode(paraphrases, skip_special_tokens=True)
```

And the output will be something like:
```shell
['Yarın toplantı ne zaman başlıyor?',
 'Yarın toplantı saat kaçta başlıyor?',
 'Yarın toplantı saat kaçta başlar?',
 'Yarın toplantı ne zaman başlayacak?',
 'Yarın toplantı ne zaman başlar?']
```

## Dataset
I used [TQP dataset V0.1](https://github.com/monatis/tqp) that I've published just recently. This model should be taken as as a baseline model for TQP dataset. A cleaning and further improvements in the dataset and an elaborate hyperparameter tuning may boost the performance.

## Citation
If you find the dataset or model useful for your research, [consider citation](https://zenodo.org/record/4719801#.YIbI45AzZPZ).