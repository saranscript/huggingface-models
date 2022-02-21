This is the detoxification baseline model trained on the [train](https://github.com/skoltech-nlp/russe_detox_2022/blob/main/data/input/train.tsv) part of "RUSSE 2022: Russian Text Detoxification Based on Parallel Corpora" competition. The source sentences are Russian toxic messages from Odnoklassniki, Pikabu, and Twitter platforms. The base model is [ruT5](https://huggingface.co/sberbank-ai/ruT5-base) provided from Sber.

**How to use**
```python
from transformers import T5ForConditionalGeneration, AutoTokenizer

base_model_name = 'sberbank-ai/ruT5-base'
model_name = 'SkolkovoInstitute/ruT5-base-detox'

tokenizer = AutoTokenizer.from_pretrained(base_model_name)
model = T5ForConditionalGeneration.from_pretrained(model_name)
```

## Licensing Information

[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png