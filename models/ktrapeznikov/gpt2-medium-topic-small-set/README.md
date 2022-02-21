---
language: 
- en
thumbnail:
widget:
 - text: "topic climate source"
---

# GPT2-medium-topic-news

## Model description

GPT2-medium fine tuned on a small news corpus conditioned on a topic, source, title

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

## Sample Output

>[topic] military [source] straitstimes [title] Trump signs bill on military aid to Israel [body]  WASHINGTON (AFP) - US President Donald Trump signed into law Thursday (April 24) legislation to provide more than US$15 billion (S$20.43 billion) in military aid to Israel, a move the Obama administration had resisted for political reasons. The White House did not immediately respond to a request for comment on the Israel measure, which Trump had sought unsuccessfully to block during the Obama pres ... 

>[topic] military [source] straitstimes [title] Hong Kong's leaders to discuss new travel restrictions as lockdown looms [body]  HONG KONG (REUTERS) - Hong Kong authorities said they would hold a meeting of the Legislative Council on Monday (July 21) to discuss new travel restrictions on Hong Kong residents, as the city reported a record daily increase in coronavirus cases.  The authorities said they would consider the proposal after meeting government chiefs and reviewing other measures. The co ... 

>[topic] military [source] straitstimes [title] Trump signs Bill that gives US troops wider latitude to conduct operations abroad [body]  WASHINGTON (AFP) - US President Donald Trump on Thursday (July 23) signed a controversial law that gives US troops more leeway to conduct operations abroad, as he seeks to shore up the embattled government's defences against the coronavirus pandemic and stave off a potentially devastating election defeat. Trump's signature Bill, named after his late father's l ... 

>[topic] military [source] straitstimes [title] China's Foreign Ministry responds to Japan's statement on South China Sea: 'No one should assume the role of mediator' [body]  BEIJING (AFP) - The Ministry of Foreign Affairs on Tuesday (Oct 18) told Japan to stop taking sides in the South China Sea issue and not interfere in the bilateral relationship, as Japan said it would do "nothing". Foreign Ministry spokesman Zhao Lijian told reporters in Beijing that the Chinese government's position on the ... 

>[topic] military [source] straitstimes [title] US warns North Korea on potential nuclear strike [body]  WASHINGTON - The United States warned North Korea last Friday that an attack by the North could be a "provocation" that would have "a devastating effect" on its security, as it took aim at Pyongyang over its continued efforts to develop weapons of mass destruction. US Secretary of State Mike Pompeo was speaking at the conclusion of a White House news conference when a reporter asked him how t ... 

>[topic] military [source] straitstimes [title] China calls Hong Kong to halt 'illegal and illegal military acts' [body]  WASHINGTON • Chinese Foreign Ministry spokeswoman Hua Chunying said yesterday that Hong Kong must stop 'illegal and illegal military acts' before Beijing can recognise the city as its own. In her annual State Councillor's speech, Ms Hua made the case for Hong Kong to resume Hong Kong's status as a semi-autonomous city, and vowed to use its "great power position to actively an ... 



## Training data


## Training procedure
