DPR context encoder for Biomedical slot filling see https://arxiv.org/abs/2109.08564 for details.

Load with:

```python
from transformers import DPRContextEncoder, DPRContextEncoderTokenizerFast
ctx_encoder = DPRContextEncoder.from_pretrained('healx/biomedical-dpr-ctx-encoder')
ctx_tokenizer = DPRContextEncoderTokenizerFast.from_pretrained('facebook/dpr-ctx_encoder-single-nq-base')
```