---
language:
- en
tags:
- image-to-text
license: mit
datasets:
- coco2017
---

# Vit2-DistilGPT2
This model takes in an image and outputs a caption. It was trained using the Coco dataset and the full training script can be found in [this kaggle kernel](https://www.kaggle.com/sachin/visionencoderdecoder-model-training)

## Usage
```python
import Image
from transformers import AutoModel, GPT2Tokenizer, ViTFeatureExtractor
model = AutoModel.from_pretrained("sachin/vit2distilgpt2")
vit_feature_extractor = ViTFeatureExtractor.from_pretrained("google/vit-base-patch16-224-in21k")
# make sure GPT2 appends EOS in begin and end
def build_inputs_with_special_tokens(self, token_ids_0, token_ids_1=None):
    outputs = [self.bos_token_id] + token_ids_0 + [self.eos_token_id]
    return outputs
    
GPT2Tokenizer.build_inputs_with_special_tokens = build_inputs_with_special_tokens
gpt2_tokenizer = GPT2Tokenizer.from_pretrained("distilgpt2")
# set pad_token_id to unk_token_id -> be careful here as unk_token_id == eos_token_id == bos_token_id
gpt2_tokenizer.pad_token = gpt2_tokenizer.unk_token
image = (Image.open(image_path).convert("RGB"), return_tensors="pt").pixel_values
encoder_outputs = model.generate(image.unsqueeze(0))
generated_sentences = gpt2_tokenizer.batch_decode(encoder_outputs, skip_special_tokens=True)
```
Note that the output sentence may be repeated, hence a post processing step may be required.

## Bias Warning
This model may be biased due to dataset, lack of long training and the model itself. The following gender bias is an example.
![](https://i.imgur.com/9zVN022.png)

## Results
<iframe src="https://wandb.ai/sachinruk/Vit2GPT2/reports/Shared-panel-22-01-27-23-01-56--VmlldzoxNDkyMTM3?highlightShare" style="border:none;height:1024px;width:100%">

