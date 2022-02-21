DPR query encoder for Biomedical slot filling see https://arxiv.org/abs/2109.08564 for details.

Load with:

```python
from transformers import DPRQuestionEncoder, DPRQuestionEncoderTokenizerFast
qry_encoder = DPRQuestionEncoder.from_pretrained('healx/biomedical-dpr-qry-encoder')
qry_tokenizer = DPRQuestionEncoderTokenizer.from_pretrained('facebook/dpr-question_encoder-single-nq-base')
```