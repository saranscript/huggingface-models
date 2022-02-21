This is an example of how a kenLM model can be downloaded with [PyCTCDecode](https://github.com/kensho-technologies/pyctcdecode) .

Simply run the following code:

```python
from pyctcdecode import BeamSearchDecoderCTC

decoder = BeamSearchDecoderCTC.load_from_hf_hub("kensho/beamsearch_decoder_dummy")
```

The model was created by [Patrick von Platen](https://huggingface.co/patrickvonplaten) for demonstration purposes.