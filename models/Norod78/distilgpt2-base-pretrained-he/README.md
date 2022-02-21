---
language: he

thumbnail: https://avatars1.githubusercontent.com/u/3617152?norod.jpg
widget:
- text: "עוד בימי קדם"
- text: "קוראים לי דורון ואני מעוניין ל"
- text: "קוראים לי איציק ואני חושב ש"
- text: "החתול שלך מאוד חמוד ו"

license: mit
---

# hebrew-distilgpt2

A tiny GPT2 based Hebrew text generation model trained on a TPUv3-8 which was made avilable to me via the [TPU Research Cloud](https://sites.research.google/trc/) Program.

## Dataset

oscar / unshuffled_deduplicated_he - [Homepage](https://oscar-corpus.com) | [Dataset Permalink](https://huggingface.co/datasets/viewer/?dataset=oscar&config=unshuffled_deduplicated_he)

The Open Super-large Crawled ALMAnaCH coRpus is a huge multilingual corpus obtained by language classification and filtering of the Common Crawl corpus using the goclassy architecture.

## Training

* Done on a TPUv3-8 VM using [Huggingface's clm-flax example script](https://github.com/huggingface/transformers/blob/master/examples/flax/language-modeling/run_clm_flax.py) <BR>
* I have made a list of items which might make it easier for other to use this script. The list was posted to [This discussion forum](https://discuss.huggingface.co/t/ideas-for-beginner-friendlier-tpu-vm-clm-training/8351)

## Usage


#### Simple usage sample code

```python


from transformers import AutoTokenizer, AutoModelForCausalLM
  
#pip install tokenizers==0.10.3 transformers==4.8.0

tokenizer = AutoTokenizer.from_pretrained("Norod78/distilgpt2-base-pretrained-he")
model = AutoModelForCausalLM.from_pretrained("Norod78/distilgpt2-base-pretrained-he", pad_token_id=tokenizer.eos_token_id)

prompt_text = "הנבחרת האולימפית של ישראל זכתה השנה"
max_len = 50
sample_output_num = 3
seed = 1000

import numpy as np
import torch

device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
n_gpu = 0 if torch.cuda.is_available()==False else torch.cuda.device_count()

print(f"device: {device}, n_gpu: {n_gpu}")

np.random.seed(seed)
torch.manual_seed(seed)
if n_gpu > 0:
    torch.cuda.manual_seed_all(seed)

model.to(device)

encoded_prompt = tokenizer.encode(
    prompt_text, add_special_tokens=False, return_tensors="pt")

encoded_prompt = encoded_prompt.to(device)

if encoded_prompt.size()[-1] == 0:
        input_ids = None
else:
        input_ids = encoded_prompt

print("input_ids = " + str(input_ids))

if input_ids != None:
  max_len += len(encoded_prompt[0])
  if max_len > 1024:
    max_len = 1024

print("Updated max_len = " + str(max_len))

stop_token = "<|endoftext|>"
new_lines = "\n\n\n"

sample_outputs = model.generate(
    input_ids,
    do_sample=True, 
    max_length=max_len, 
    top_k=50, 
    top_p=0.95, 
    num_return_sequences=sample_output_num
)

print(100 * '-' + "\n\t\tOutput\n" + 100 * '-')
for i, sample_output in enumerate(sample_outputs):

  text = tokenizer.decode(sample_output, skip_special_tokens=True)
  
  # Remove all text after the stop token
  text = text[: text.find(stop_token) if stop_token else None]

  # Remove all text after 3 newlines
  text = text[: text.find(new_lines) if new_lines else None]

  print("\n{}: {}".format(i, text))
  print("\n" + 100 * '-')

```
