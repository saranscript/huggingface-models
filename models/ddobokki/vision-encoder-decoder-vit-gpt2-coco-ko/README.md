## EXAMPLE
```python
import requests
import torch
from PIL import Image
from transformers import (
    VisionEncoderDecoderModel, 
    ViTFeatureExtractor, 
    PreTrainedTokenizerFast,
)

# device setting
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')

# load feature extractor and tokenizer
encoder_model_name_or_path = "ddobokki/vision-encoder-decoder-vit-gpt2-coco-ko"
feature_extractor = ViTFeatureExtractor.from_pretrained(encoder_model_name_or_path)
tokenizer = PreTrainedTokenizerFast.from_pretrained(encoder_model_name_or_path)

# load model
model = VisionEncoderDecoderModel.from_pretrained(encoder_model_name_or_path)
model.to(device)

# inference
url = 'http://images.cocodataset.org/val2017/000000039769.jpg'
with Image.open(requests.get(url, stream=True).raw) as img:
    pixel_values = feature_extractor(images=img, return_tensors="pt").pixel_values

generated_ids = model.generate(pixel_values.to(device),num_beams=5)
generated_text = tokenizer.batch_decode(generated_ids, skip_special_tokens=True)

>> ['고양이 두마리가 담요 위에 누워 있다.']
```
