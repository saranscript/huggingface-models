---
language: 
  - ko
tags:
- classification
- sentence similarity 
license: cc-by-4.0
datasets:
- korsts
metrics:
- accuracy
- f1
- precision
- recall
---


# Similarity between two sentences (fine-tuning with KoELECTRA-Small-v3 model and KorSTS dataset)

## Usage (Amazon SageMaker inference applicable)
It uses the interface of the SageMaker Inference Toolkit as is, so it can be easily deployed to SageMaker Endpoint.

### inference_korsts.py

```python
import json
import sys
import logging
import torch
from torch import nn
from transformers import ElectraConfig
from transformers import ElectraModel, AutoTokenizer, ElectraTokenizer, ElectraForSequenceClassification

logging.basicConfig(
    level=logging.INFO, 
    format='[{%(filename)s:%(lineno)d} %(levelname)s - %(message)s',
    handlers=[
        logging.FileHandler(filename='tmp.log'),
        logging.StreamHandler(sys.stdout)
    ]
)
logger = logging.getLogger(__name__)

max_seq_length = 128
tokenizer = AutoTokenizer.from_pretrained("daekeun-ml/koelectra-small-v3-korsts")
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")


# Huggingface pre-trained model: 'monologg/koelectra-small-v3-discriminator'
def model_fn(model_path):
    ####
    # If you have your own trained model
    # Huggingface pre-trained model: 'monologg/koelectra-small-v3-discriminator'
    ####    
    #config = ElectraConfig.from_json_file(f'{model_path}/config.json')
    #model = ElectraForSequenceClassification.from_pretrained(f'{model_path}/model.pth', config=config)
    model = ElectraForSequenceClassification.from_pretrained('daekeun-ml/koelectra-small-v3-korsts')
    model.to(device)
    return model


def input_fn(input_data, content_type="application/jsonlines"):
    data_str = input_data.decode("utf-8")
    jsonlines = data_str.split("\n")
    transformed_inputs = []
    
    for jsonline in jsonlines:
        text = json.loads(jsonline)["text"]
        logger.info("input text: {}".format(text))          
        encode_plus_token = tokenizer.encode_plus(
            text,
            max_length=max_seq_length,
            add_special_tokens=True,
            return_token_type_ids=False,
            padding="max_length",
            return_attention_mask=True,
            return_tensors="pt",
            truncation=True,
        )
        transformed_inputs.append(encode_plus_token)
        
    return transformed_inputs


def predict_fn(transformed_inputs, model):
    predicted_classes = []

    for data in transformed_inputs:
        data = data.to(device)
        output = model(**data)

        prediction_dict = {}
        prediction_dict['score'] = output[0].squeeze().cpu().detach().numpy().tolist()

        jsonline = json.dumps(prediction_dict)
        logger.info("jsonline: {}".format(jsonline))        
        predicted_classes.append(jsonline)

    predicted_classes_jsonlines = "\n".join(predicted_classes)
    return predicted_classes_jsonlines


def output_fn(outputs, accept="application/jsonlines"):
    return outputs, accept
```    

### test.py 
```python
>>> from inference_korsts import model_fn, input_fn, predict_fn, output_fn
>>> with open('./samples/korsts.txt', mode='rb') as file:
>>>    model_input_data = file.read()
>>> model = model_fn()
>>> transformed_inputs = input_fn(model_input_data)
>>> predicted_classes_jsonlines = predict_fn(transformed_inputs, model)
>>> model_outputs = output_fn(predicted_classes_jsonlines)
>>> print(model_outputs[0])     

[{inference_korsts.py:44} INFO - input text: ['맛있는 라면을 먹고 싶어요', '후루룩 쩝쩝 후루룩 쩝쩝 맛좋은 라면']
[{inference_korsts.py:44} INFO - input text: ['뽀로로는 내친구', '머신러닝은 러닝머신이 아닙니다.']
[{inference_korsts.py:71} INFO - jsonline: {"score": 4.786738872528076}
[{inference_korsts.py:71} INFO - jsonline: {"score": 0.2319069355726242}
{"score": 4.786738872528076}
{"score": 0.2319069355726242}
```

### Sample data (samples/korsts.txt)
```
{"text": ["맛있는 라면을 먹고 싶어요", "후루룩 쩝쩝 후루룩 쩝쩝 맛좋은 라면"]}
{"text": ["뽀로로는 내친구", "머신러닝은 러닝머신이 아닙니다."]}
```

## References
- KoELECTRA: https://github.com/monologg/KoELECTRA
- KorNLI and KorSTS Dataset: https://github.com/kakaobrain/KorNLUDatasets