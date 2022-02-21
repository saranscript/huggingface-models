West et al.'s model from their "reflective decoding" paper. 

Sample usage: 

```python
import torch
from modeling_opengpt2 import OpenGPT2LMHeadModel
from padded_encoder import Encoder

path_to_backward = 'danyaljj/opengpt2_pytorch_backward'

encoder = Encoder()
model_backward = OpenGPT2LMHeadModel.from_pretrained(path_to_backward)

input = "until she finally won."
input_ids = encoder.encode(input)
input_ids = torch.tensor([input_ids[::-1] ], dtype=torch.int)
print(input_ids)

output = model_backward.generate(input_ids)

output_text = encoder.decode(output.tolist()[0][::-1])

print(output_text)
```

Download the additional files from here: https://github.com/peterwestuw/GPT2ForwardBackward

