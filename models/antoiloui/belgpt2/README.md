---
language:
- fr
license:
- mit
widget:
- text: "Hier, Elon Musk a"
- text: "Pourquoi a-t-il"
- text: "Tout à coup, elle"
---

# Belgian GPT-2 🇧🇪

**A GPT-2 model pre-trained on a very large and heterogeneous French corpus (~60Gb).**

## Usage

You can use BelGPT-2 with [🤗 transformers](https://github.com/huggingface/transformers):

```python
import torch
from transformers import GPT2Tokenizer, GPT2LMHeadModel

# Load pretrained model and tokenizer
model = GPT2LMHeadModel.from_pretrained("antoiloui/belgpt2")
tokenizer = GPT2Tokenizer.from_pretrained("antoiloui/belgpt2")

# Generate a sample of text
model.eval()
output = model.generate(
            bos_token_id=random.randint(1,50000),
            do_sample=True,   
            top_k=50, 
            max_length=100,
            top_p=0.95, 
            num_return_sequences=1
)

# Decode it
decoded_output = []
for sample in output:
    decoded_output.append(tokenizer.decode(sample, skip_special_tokens=True))
print(decoded_output)
```

## Data

Below is the list of all French copora used to pre-trained the model:

| Dataset | `$corpus_name` | Raw size | Cleaned size |
| :------|   :--- | :---: | :---: | 
| CommonCrawl |  `common_crawl`   |  200.2 GB   |  40.4 GB   |
| NewsCrawl |   `news_crawl`  |   10.4 GB  |  9.8 GB   |
| Wikipedia |   `wiki`  |   19.4 GB  |  4.1 GB   |
| Wikisource |   `wikisource`  |  4.6  GB  |  2.3 GB   |
| Project Gutenberg |  `gutenberg`   |  1.3 GB   |  1.1 GB   |
| EuroParl |  `europarl`   |  289.9 MB   |   278.7 MB  |
| NewsCommentary |  `news_commentary`   |   61.4 MB  |  58.1 MB   |
| **Total** |     |   **236.3 GB**  |  **57.9 GB**   |

## Documentation

Detailed documentation on the pre-trained model, its implementation, and the data can be found [here](https://github.com/antoiloui/belgpt2/blob/master/docs/index.md).

## Citation

For attribution in academic contexts, please cite this work as:

```
@misc{louis2020belgpt2,
  author = {Louis, Antoine},
  title = {{BelGPT-2: a GPT-2 model pre-trained on French corpora.}},
  year = {2020},
  howpublished = {\url{https://github.com/antoiloui/belgpt2}},
}
```