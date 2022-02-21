# LayoutXLM finetuned on XFUN.ja

```python
import torch
import numpy as np
from PIL import Image, ImageDraw, ImageFont
from pathlib import Path
from itertools import chain
from tqdm.notebook import tqdm
from pdf2image import convert_from_path
from transformers import LayoutXLMProcessor, LayoutLMv2ForTokenClassification

import os
os.environ["TOKENIZERS_PARALLELISM"] = "false"

labels = [
    'O',
    'B-QUESTION',
    'B-ANSWER',
    'B-HEADER',
    'I-ANSWER',
    'I-QUESTION',
    'I-HEADER'
]
id2label = {v: k for v, k in enumerate(labels)}
label2id = {k: v for v, k in enumerate(labels)}

def unnormalize_box(bbox, width, height):
    return [
         width * (bbox[0] / 1000),
         height * (bbox[1] / 1000),
         width * (bbox[2] / 1000),
         height * (bbox[3] / 1000),
    ]

def iob_to_label(label):
    label = label[2:]
    if not label:
        return 'other'
    return label

label2color = {'question':'blue', 'answer':'green', 'header':'orange', 'other':'violet'}

def infer(image, processor, model, label2color):
    # Use this if you're loading images
    # image = Image.open(img_path).convert("RGB")
    
    image = image.convert("RGB") # loading PDFs
    encoding = processor(image, return_offsets_mapping=True, return_tensors="pt", truncation=True, max_length=514)
    offset_mapping = encoding.pop('offset_mapping')
    outputs = model(**encoding)
    predictions = outputs.logits.argmax(-1).squeeze().tolist()
    token_boxes = encoding.bbox.squeeze().tolist()

    width, height = image.size
    is_subword = np.array(offset_mapping.squeeze().tolist())[:,0] != 0

    true_predictions = [id2label[pred] for idx, pred in enumerate(predictions) if not is_subword[idx]]
    true_boxes = [unnormalize_box(box, width, height) for idx, box in enumerate(token_boxes) if not is_subword[idx]]
    draw = ImageDraw.Draw(image)

    font = ImageFont.load_default()

    for prediction, box in zip(true_predictions, true_boxes):
        predicted_label = iob_to_label(prediction).lower()
        draw.rectangle(box, outline=label2color[predicted_label])
        draw.text((box[0]+10, box[1]-10), text=predicted_label, fill=label2color[predicted_label], font=font)

    return image

processor = LayoutXLMProcessor.from_pretrained('beomus/layoutxlm')
model = LayoutLMv2ForTokenClassification.from_pretrained("beomus/layoutxlm")


# imgs = [img_path for img_path in Path('/your/path/imgs/').glob('*.jpg')]

imgs = [convert_from_path(img_path) for img_path in Path('/your/path/pdfs/').glob('*.pdf')]
imgs = list(chain.from_iterable(imgs))


outputs = [infer(img_path, processor, model, label2color) for img_path in tqdm(imgs)]

# type(outputs[0]) -> PIL.Image.Image
```