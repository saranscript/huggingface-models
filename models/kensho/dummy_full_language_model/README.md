This is an example of how a kenLM model can be downloaded with [PyCTCDecode](https://github.com/kensho-technologies/pyctcdecode) .

Simply run the following code:

```python
from pyctcdecode import LanguageModel

language_model = LanguageModel.load_from_hf_hub("kensho/dummy_full_language_model")
```

The model was created by [Patrick von Platen](https://huggingface.co/patrickvonplaten) for demonstration purposes.