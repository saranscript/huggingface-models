---
language: 
- nl
tags:
- mbart
- bart
- summarization
datasets:
- ml6team/cnn_dailymail_nl
---
# mbart-large-cc25-cnn-dailymail-nl
## Model description
Finetuned version of [mbart](https://huggingface.co/facebook/mbart-large-cc25). We also wrote a **blog post** about this model [here](https://blog.ml6.eu/)
## Intended uses & limitations
It's meant for summarizing Dutch news articles.
#### How to use
```python
import transformers
undisputed_best_model = transformers.MBartForConditionalGeneration.from_pretrained(
    "ml6team/mbart-large-cc25-cnn-dailymail-nl-finetune"
)
tokenizer = transformers.MBartTokenizer.from_pretrained("facebook/mbart-large-cc25")
summarization_pipeline = transformers.pipeline(
    task="summarization",
    model=undisputed_best_model,
    tokenizer=tokenizer,
)
summarization_pipeline.model.config.decoder_start_token_id = tokenizer.lang_code_to_id[
    "nl_XX"
]
article = "Kan je dit even samenvatten alsjeblief."  # Dutch
summarization_pipeline(
    article,
    do_sample=True,
    top_p=0.75,
    top_k=50,
    # num_beams=4,
    min_length=50,
    early_stopping=True,
    truncation=True,
)[0]["summary_text"]
```
## Training data
Finetuned [mbart](https://huggingface.co/facebook/mbart-large-cc25) with [this dataset](https://huggingface.co/datasets/ml6team/cnn_dailymail_nl) and another smaller dataset that we can't open source because we scraped it from the internet. For more information check out our blog post [here](https://blog.ml6.eu/).