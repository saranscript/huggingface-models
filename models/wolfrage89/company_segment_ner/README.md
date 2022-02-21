## Roberta based NER
This model will take in a new article label 3 entities [ORGS, SEGNUM, NUM]. This model is train on reuters news articles

## Try out on huggingface Spaces
https://huggingface.co/spaces/wolfrage89/company_segments_ner

## colab sample notebook
https://colab.research.google.com/drive/165utMQzYVAX7-aQjWjpmPHwHpdKTaHBa?usp=sharing

## How to use
```python

from transformers import pipeline

# Minimum code
sentence = """Exxon Mobil Corporation is engaged in energy business. The Company is engaged in the exploration, production, trade, transportation and sale of crude oil and natural gas, and the manufacture, transportation and sale of crude oil, natural gas, petroleum products, petrochemicals and a range of specialty products. The Company's segments include Upstream, Downstream, Chemical, and Corporate and Financing. The Upstream segment operates to explore for and produce crude oil and natural gas. The Downstream manufactures, trades and sells petroleum products. The refining and supply operations consists of a global network of manufacturing plants, transportation systems, and distribution centers that provide a range of fuels, lubricants and other products and feedstocks to its customers around the world. The Chemical segment manufactures and sells petrochemicals. The Chemical business supplies olefins, polyolefins, aromatics, and a variety of other petrochemicals."""


model = pipeline('ner', "wolfrage89/company_segment_ner")
model_output = model(sentence)

print(model_ouput)
# [{'entity': 'B-ORG', 'score': 0.99996805, 'index': 1, 'word': 'Ex', 'start': 0, 'end': 2}, {'entity': 'I-ORG', 'score': 0.99971646, 'index': 2, 'word': 'xon', 'start': 2, 'end': 5}, ....]


# Sample helper function if you want to use 
def ner_prediction(model, sentence):
    entity_map = {
        "B-ORG":"ORG",
        "B-SEG":"SEG",
        "B-SEGNUM":"SEGNUM"
    }
    results = []
    model_output = model(sentence)

    accumulate = ""
    current_class = None
    start = 0
    end = 0
    for item in model_output:
        if item['entity'].startswith("B"):
            if len(accumulate) >0:
                results.append((current_class, accumulate, start, end))
            accumulate = item['word'].lstrip("Ġ")
            current_class = entity_map[item['entity']]
            start=item['start']
            end = item['end']
            
        else:
            if item['word'].startswith("Ġ"):
                accumulate+=" "+item['word'].lstrip("Ġ")
                
            else:
                accumulate+=item['word']
            end = item['end']

    # clear last cache
    if len(accumulate)>0:
         results.append((current_class, accumulate, start, end))

    return results

```