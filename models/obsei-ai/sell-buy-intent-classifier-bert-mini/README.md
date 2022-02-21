---
language: "en"
tags:
- buy-intent
- sell-intent
- consumer-intent
widget:
- text: "Can you please share pictures for Face Shields ? We are looking for large quantity pcs"
---
# Buy vs Sell Intent Classifier
| Train Loss    | Validation Acc.| Test Acc.|
| ------------- |:-------------: | -----:   |
| 0.013      | 0.988  | 0.992    |

# Sample Intents for Testings
LABEL_0 => **"SELLING_INTENT"** <br/>
LABEL_1 => **"BUYING_INTENT"**

## Buying Intents
- I am interested in this style of PGN-ES-D-6150 /Direct drive energy saving servo motor price and in doing business with you. Could you please send me the quotation
- Hi, I am looking for a supplier of calcium magnesium carbonate fertilizer. Can you send 1 bag sample via air freight to the USA?
- I am looking for the purple ombre dress with floral bodice in a size 12 for my wedding in June this year
- we are interested in your Corned Beef. do you have any quality assurance certificates? looking forward to hearing from you.
- I would like to know if pet nail clippers are of high quality. And if you would send a free sample?

## Selling Intents
- Black full body massage chair for sale.
- Boiler over 7 years old
- Polyester trousers black, size 24.
- Oliver Twist £1, German Dictionary 50p (Cold War s0ld), Penguin Plays £1, post by arrangement. The bundle price is £2. Will separate (Twelfth Night and Sketch B&W Sold)
- Brand new Royal Doulton bone China complete Dinner Service comprising 55 pieces including coffee pot and cups. (6 PLACE SETTING) ! 'Diana' design delicate pattern.


## Usage in Transformers

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained("obsei-ai/sell-buy-intent-classifier-bert-mini")

model = AutoModelForSequenceClassification.from_pretrained("obsei-ai/sell-buy-intent-classifier-bert-mini")
```

## <p style='color:red'>Due to the privacy reasons, I unfortunately can't share the dataset and its splits.</p>