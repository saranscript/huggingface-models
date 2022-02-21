# Telugu Question-Answering model trained on Tydiqa dataset from Google

#### How to use
Use the below script from your python terminal as the web interface for inference has few encoding issues for Telugu
```python
from transformers.pipelines import pipeline, AutoModelForQuestionAnswering, AutoTokenizer
model = AutoModelForQuestionAnswering.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained("kuppuluri/telugu_bertu_tydiqa",
                                          clean_text=False,
                                          handle_chinese_chars=False,
                                          strip_accents=False,
                                          wordpieces_prefix='##')
nlp = pipeline('question-answering', model=model, tokenizer=tokenizer)
result = nlp({'question': question, 'context': context})
```

## Training data
I used Tydiqa Telugu data from Google https://github.com/google-research-datasets/tydiqa

PS: If you find my model useful, I would appreciate a note from you as it would encourage me to continue improving it and also add new models.
