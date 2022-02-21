---
language:
- en
tags:
- simplification
license: apache-2.0
datasets:
- cnn_dailymail
widget:
- text: "A capsule containing asteroid soil samples landed in the Australian Outback. The precision required to carry out the mission thrilled many.<|endoftext|>"
  example_title: "Example 1"
---

# Try out in the Hosted inference API
In the right panel, you can try the model (although it only handles a short sequence length).
Feel free to try Example 1, and modify it to inspect model ability.


# Model Loading

The model can be loaded in the following way:
```
from transformers import AutoTokenizer, AutoModelForCausalLM
import torch

tokenizer = AutoTokenizer.from_pretrained("philippelaban/keep_it_simple")
kis_model = AutoModelForCausalLM.from_pretrained("philippelaban/keep_it_simple")
```

# Example use

And then used by first inputting a paragraph for simplification, followed by a `bos_token` to indicate to the model to start simplifying.
Imagine we want to simplify the following paragraph:
```
A small capsule containing asteroid soil samples that was dropped from 136,700 miles in space
by Japan's Hayabusa2 spacecraft landed as planned in the Australian Outback on December 6.
The extremely high precision required to carry out the mission thrilled many in Japan,
who said they took pride in its success.
```

The following code can be run:
```
paragraph = """A small capsule containing asteroid soil samples that was dropped from 136,700 miles in space by Japan's Hayabusa2 spacecraft landed as planned in the Australian Outback on December 6. The extremely high precision required to carry out the mission thrilled many in Japan, who said they took pride in its success."""

start_id = tokenizer.bos_token_id
tokenized_paragraph = [(tokenizer.encode(text=paragraph) + [start_id])]
input_ids = torch.LongTensor(tokenized_paragraph)

output_ids = kis_model.generate(input_ids, max_length=150, num_beams=4, do_sample=True, num_return_sequences=8)
output_ids = output_ids[:, input_ids.shape[1]:]
output = tokenizer.batch_decode(output_ids)
output = [o.replace(tokenizer.eos_token, "") for o in output]

for o in output:
    print("----")
    print(o)
```

# Example output

When run, an output similar to the following should be obtained:

A small capsule containing samples of asteroid soil that was dropped from 136,700 miles, Japan's Hayabusa2 space probe, landed as planned on December 6. The mission was extremely precise, said many in Japan, and they took pride in its success.

A small capsule containing samples of asteroid soil that was dropped from 136,700 miles, Japan's Hayabusa2 space probe, landed as planned on December 6. The mission was extremely precise and well thought-out, said many in Japan, who took pride in the mission.

A small capsule containing soil samples that was dropped from 136,700 miles, Japan's Hayabusa2 space probe, landed as planned on December 6. The mission was designed to test the performance of the country's space fleet, which many said took pride in its success.

A small capsule containing soil samples that was dropped from 136,700 miles in space by Japan's Hayabusa2 probe was followed by a landing on the Outback. The precise timing of the mission thrilled many in Japan, who said they took pride in its success.

# Github repo

You can access more information, access to the scoring function, the training script, or an example training log on the Github repo:
https://github.com/tingofurro/keep_it_simple