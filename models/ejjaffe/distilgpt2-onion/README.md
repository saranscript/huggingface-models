# Load the Model

```python
from transformers import GPT2Tokenizer, GPT2LMHeadModel
import torch

# start and end tokens for generation
START_TKN = "<|startoftext|>"
END_TKN = "<|endoftext|>"

# fine tuned on onion dataset w/ distilgpt2
tokenizer = GPT2Tokenizer.from_pretrained("distilgpt2")
model = GPT2LMHeadModel.from_pretrained("distilgpt2")

# use gpu if available
device = "cpu"
  if torch.cuda.is_available():
    device = "cuda"

model = model.to(device)

# get 70th epoch (decent results)
epoch = 70
modelpath = f'distilgpt2_onion_{epoch}.pt' 

# load model
model.load_state_dict(torch.load(modelpath))
```

