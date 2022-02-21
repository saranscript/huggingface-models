
The purpose of this repo is to show the usefulness of saving the normalization operation used during the tokenizer training

```python
from transformers import AutoTokenizer

text = "This is a text with àccënts and CAPITAL LETTERS"
tokenizer = AutoTokenizer.from_pretrained("albert-large-v2")
print(tokenizer.convert_ids_to_tokens(tokenizer.encode(text)))

# ['[CLS]', '▁this', '▁is', '▁a', '▁text', '▁with', '▁accent', 's', '▁and', '▁capital', '▁letters', '[SEP]']
tokenizer = AutoTokenizer.from_pretrained("huggingface-course/albert-tokenizer-without-normalizer")
print(tokenizer.convert_ids_to_tokens(tokenizer.encode(text)))
# ['[CLS]', '▁', '<unk>', 'his', '▁is', '▁a', '▁text', '▁with', '▁', '<unk>', 'cc', '<unk>', 'nts', '▁and', '▁', '<unk>', '▁', '<unk>', '[SEP]']
```