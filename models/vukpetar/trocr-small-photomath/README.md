## TrOCR (small-sized model, fine-tuned on Synthetic Math Expression Dataset)
TrOCR model fine-tuned on the Synthetic Math Expression Dataset. It was introduced in the paper [TrOCR: Transformer-based Optical Character Recognition with Pre-trained Models](https://arxiv.org/abs/2109.10282) by Li et al. and first released in [this repository](https://github.com/microsoft/unilm/tree/master/trocr).

Disclaimer: The team releasing TrOCR did not write a model card for this model so this model card has been written by the Hugging Face team.

## Model description
The TrOCR model is an encoder-decoder model, consisting of an image Transformer as encoder, and a text Transformer as decoder. The image encoder was initialized from the weights of BEiT, while the text decoder was initialized from the weights of RoBERTa.

Images are presented to the model as a sequence of fixed-size patches (resolution 16x16), which are linearly embedded. One also adds absolute position embeddings before feeding the sequence to the layers of the Transformer encoder. Next, the Transformer text decoder autoregressively generates tokens.

## Intended uses & limitations
You can use the raw model for optical character recognition (OCR) on single text-line images. See the model hub to look for fine-tuned versions on a task that interests you.

## How to use
Here is how to use this model in PyTorch:
```python
from transformers import VisionEncoderDecoderModel, AutoFeatureExtractor, AutoTokenizer
from PIL import Image
import requests

# load image from the IAM database
url = 'https://drive.google.com/uc?export=view&id=15dUjO44YDe1Agw_Qi8MyODRHpUFaCFw-'
image = Image.open(requests.get(url, stream=True).raw).convert("RGB")

feature_extractor = AutoFeatureExtractor.from_pretrained('vukpetar/trocr-small-photomath')
tokenizer = AutoTokenizer.from_pretrained("vukpetar/trocr-small-photomath")
model = VisionEncoderDecoderModel.from_pretrained('vukpetar/trocr-small-photomath')
pixel_values = feature_extractor(images=image, return_tensors="pt").pixel_values

generated_ids = model.generate(pixel_values)
generated_text = tokenizer.batch_decode(generated_ids, skip_special_tokens=True)[0]
```


## BibTeX entry and citation info
    @misc{li2021trocr,
      title={TrOCR: Transformer-based Optical Character Recognition with Pre-trained Models}, 
      author={Minghao Li and Tengchao Lv and Lei Cui and Yijuan Lu and Dinei Florencio and Cha Zhang and Zhoujun Li and Furu Wei},
      year={2021},
      eprint={2109.10282},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
    }