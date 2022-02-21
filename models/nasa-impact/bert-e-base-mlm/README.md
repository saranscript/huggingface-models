This model is further trained on top of scibert-base using masked language modeling loss (MLM). The corpus is roughly 270,000 earth science-based publications.

The tokenizer used is AutoTokenizer, which is trained on the same corpus.

Stay tuned for further downstream task tests and updates to the model.

in the works
- MLM + NSP task loss
- Add more data sources for training
- Test using downstream tasks
