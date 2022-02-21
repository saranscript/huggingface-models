 ---
language: 
- en
thumbnail:
widget:
 - text: "topic climate source washington post title "
---

# GPT2-medium-topic-news

## Model description

GPT2-medium fine tuned on a largish news corpus conditioned on a topic, source, title

## Intended uses & limitations

#### How to use

To generate a news article text conditioned on a topic, source, title or some subsets, prompt model with: 
```python
f"topic {topic} source"
f"topic {topic} source {source} title"
f"topic {topic} source {source} title {title} body"
```

Try the following tags for `topic: climate, weather, vaccination`.

Zero shot generation works pretty well as long as `topic` is a single word and not too specific.

```python
device = "cuda:0"
tokenizer = AutoTokenizer.from_pretrained("ktrapeznikov/gpt2-medium-topic-small-set")
model = AutoModelWithLMHead.from_pretrained("ktrapeznikov/gpt2-medium-topic-small-set")
model.to(device)
topic = "climate"
prompt = tokenizer(f"topic {topics} source straitstimes title", return_tensors="pt")
out = model.generate(prompt["input_ids"].to(device), do_sample=True,max_length=500, early_stopping=True, top_p=.9)
print(tokenizer.decode(out[0].cpu(), skip_special_tokens=True))
```