---
language: da
license: cc-by-4.0
---

# Danish ConvBERT medium small (cased)

[ConvBERT](https://arxiv.org/abs/2008.02496) model pretrained on a custom Danish corpus (~17.5gb). 
For details regarding data sources and training procedure, along with benchmarks on downstream tasks, go to: https://github.com/sarnikowski/danish_transformers 

## Usage

```python
from transformers import ConvBertTokenizer, ConvBertModel

tokenizer = ConvBertTokenizer.from_pretrained("sarnikowski/convbert-medium-small-da-cased")
model = ConvBertModel.from_pretrained("sarnikowski/convbert-medium-small-da-cased")
```

## Questions?

If you have any questions feel free to open an issue on the [danish_transformers](https://github.com/sarnikowski/danish_transformers) repository, or send an email to p.sarnikowski@gmail.com
