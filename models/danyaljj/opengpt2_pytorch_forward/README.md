West et al.'s model from their "reflective decoding" paper. 

Sample usage: 

```python
import torch
from modeling_opengpt2 import OpenGPT2LMHeadModel
from padded_encoder import Encoder

path_to_forward = 'danyaljj/opengpt2_pytorch_forward'

encoder = Encoder()
model_backward = OpenGPT2LMHeadModel.from_pretrained(path_to_forward)

input = "She tried to win but"
input_ids = encoder.encode(input)
input_ids = torch.tensor([input_ids ], dtype=torch.int)
print(input_ids)

output = model_backward.generate(input_ids)

output_text = encoder.decode(output.tolist()[0])

print(output_text)
```

Download the additional files from here: https://github.com/peterwestuw/GPT2ForwardBackward

