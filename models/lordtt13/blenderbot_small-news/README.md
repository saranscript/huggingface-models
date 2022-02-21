---
language: en
---

## BlenderBotSmall-News: Small version of a state-of-the-art open source chatbot, trained on custom summaries

### Details of BlenderBotSmall

The **BlenderBotSmall** model was presented in [A state-of-the-art open source chatbot](https://ai.facebook.com/blog/state-of-the-art-open-source-chatbot/) by *Facebook AI* and here are it's details:

- Facebook AI has built and open-sourced BlenderBot, the largest-ever open-domain chatbot. It outperforms others in terms of engagement and also feels more human, according to human evaluators.
- The culmination of years of research in conversational AI, this is the first chatbot to blend a diverse set of conversational skills — including empathy, knowledge, and personality — together in one system.
- We achieved this milestone through a new chatbot recipe that includes improved decoding techniques, novel blending of skills, and a model with 9.4 billion parameters, which is 3.6x more than the largest existing system.

### Details of the downstream task (Summarization) - Dataset 📚

A custom dataset was used, which was hand prepared by [SmokeTrees Digital](https://github.com/smoke-trees) AI engineers. This data contains long texts and summaries.

### Model training

The training script is present [here](https://github.com/lordtt13/transformers-experiments/blob/master/Custom%20Tasks/fine-tune-blenderbot_small-for-summarization.ipynb).

### Pipelining the Model

```python
model = transformers.BlenderbotSmallForConditionalGeneration.from_pretrained('lordtt13/blenderbot_small-news')

tokenizer = transformers.BlenderbotSmallTokenizer.from_pretrained("lordtt13/blenderbot_small-news")

nlp_fill = transformers.pipeline('summarization', model = model, tokenizer = tokenizer)
nlp_fill('The CBI on Saturday booked four former officials of Syndicate Bank and six others for cheating, forgery, criminal conspiracy and causing ₹209 crore loss to the state-run bank. The accused had availed home loans and credit from Syndicate Bank on the basis of forged and fabricated documents. These funds were fraudulently transferred to the companies owned by the accused persons.', min_length=5, max_length=40)

# Output:
# [{'summary_text': 'marize: the cbi booked four former officials of syndicate bank and six others for cheating , forgery , criminal conspiracy and causing 209 crore loss to the staterun bank'}]
```

> Created by [Tanmay Thakur](https://github.com/lordtt13) | [LinkedIn](https://www.linkedin.com/in/tanmay-thakur-6bb5a9154/)
