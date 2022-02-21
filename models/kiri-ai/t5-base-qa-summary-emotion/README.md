---
language:
- en
tags:
- question-answering
- emotion-detection
- summarisation
license: apache-2.0
datasets:
- coqa
- squad_v2
- go_emotions
- cnn_dailymail
metrics:
- f1
pipeline_tag: text2text-generation
widget:
- text: 'q: Who is Elon Musk? a: an entrepreneur q: When was he born? c: Elon Musk
    is an entrepreneur born in 1971. </s>'
- text: 'emotion: I hope this works! </s>'
---
# T5 Base with QA + Summary + Emotion

## Dependencies

Requires transformers>=4.0.0

## Description

This model was finetuned on the CoQa, Squad 2, GoEmotions and CNN/DailyMail.

It achieves a score of **F1 79.5** on the Squad 2 dev set and a score of **F1 70.6** on the CoQa dev set.

Summarisation and emotion detection has not been evaluated yet.

## Usage

### Question answering

#### With Transformers

```python
from transformers import T5ForConditionalGeneration, T5Tokenizer
model = T5ForConditionalGeneration.from_pretrained("kiri-ai/t5-base-qa-summary-emotion")
tokenizer = T5Tokenizer.from_pretrained("kiri-ai/t5-base-qa-summary-emotion")

def get_answer(question, prev_qa, context):
    input_text = [f"q: {qa[0]} a: {qa[1]}" for qa in prev_qa]
    input_text.append(f"q: {question}")
    input_text.append(f"c: {context}")
    input_text = " ".join(input_text)
    features = tokenizer([input_text], return_tensors='pt')
    tokens = model.generate(input_ids=features['input_ids'], 
            attention_mask=features['attention_mask'], max_length=64)
    return tokenizer.decode(tokens[0], skip_special_tokens=True)

print(get_answer("Why is the moon yellow?", "I'm not entirely sure why the moon is yellow.")) # unknown

context = "Elon Musk left OpenAI to avoid possible future conflicts with his role as CEO of Tesla."

print(get_answer("Why not?", [("Does Elon Musk still work with OpenAI", "No")], context)) # to avoid possible future conflicts with his role as CEO of Tesla
```

#### With Kiri

```python
from kiri.models import T5QASummaryEmotion

context = "Elon Musk left OpenAI to avoid possible future conflicts with his role as CEO of Tesla."
prev_qa = [("Does Elon Musk still work with OpenAI", "No")]
model = T5QASummaryEmotion()

# Leave prev_qa blank for non conversational question-answering
model.qa("Why not?", context, prev_qa=prev_qa)
> "to avoid possible future conflicts with his role as CEO of Tesla"
```

### Summarisation

#### With Transformers

```python
from transformers import T5ForConditionalGeneration, T5Tokenizer
model = T5ForConditionalGeneration.from_pretrained("kiri-ai/t5-base-qa-summary-emotion")
tokenizer = T5Tokenizer.from_pretrained("kiri-ai/t5-base-qa-summary-emotion")

def summary(context):
    input_text = f"summarize: {context}"
    features = tokenizer([input_text], return_tensors='pt')
    tokens = model.generate(input_ids=features['input_ids'], 
            attention_mask=features['attention_mask'], max_length=64)
    return tokenizer.decode(tokens[0], skip_special_tokens=True)
```

#### With Kiri

```python
from kiri.models import T5QASummaryEmotion

model = T5QASummaryEmotion()

model.summarise("Long text to summarise")
> "Short summary of long text"
```

### Emotion detection

#### With Transformers

```python
from transformers import T5ForConditionalGeneration, T5Tokenizer
model = T5ForConditionalGeneration.from_pretrained("kiri-ai/t5-base-qa-summary-emotion")
tokenizer = T5Tokenizer.from_pretrained("kiri-ai/t5-base-qa-summary-emotion")

def emotion(context):
    input_text = f"emotion: {context}"
    features = tokenizer([input_text], return_tensors='pt')
    tokens = model.generate(input_ids=features['input_ids'], 
            attention_mask=features['attention_mask'], max_length=64)
    return tokenizer.decode(tokens[0], skip_special_tokens=True)
```

#### With Kiri

```python
from kiri.models import T5QASummaryEmotion

model = T5QASummaryEmotion()

model.emotion("I hope this works!")
> "optimism"
```

## About us

Kiri makes using state-of-the-art models easy, accessible and scalable.

[Website](https://kiri.ai) | [Natural Language Engine](https://github.com/kiri-ai/kiri)
