---
language: 
- en
thumbnail: 
tags:
- pytorch
- google/pegasus-reddit_tifu
- summarization
- samsum
license: 
datasets:
- samsum
metrics:
- rouge
---

# Samsum Pegasus (Reddit/TIFU) for conversational summaries

## Model description

Pegasus (Reddit/TIFU) for conversational summaries trained on the samsum dataset!

## Training data

The data is the [samsum](https://huggingface.co/datasets/samsum) dataset for conversional summaries.

The initial weigths were from the [google/pegasus-reddit_tifu](https://huggingface.co/google/pegasus-reddit_tifu). The hypothesis being that it would help the convergence on the samsum dataset to have weights trained on a larger summarization dataset first like the Reddit TIFU using casual language.

## Training procedure

Used the _example/seq2seq/run_summarization.py_ script from the transformers source _4.5.0dev0_.

  n_epochs: 3,\
  batch_size: 8, \
  max_source_length: 256,\
  max_target_length: 128

## Eval results

    eval_gen_len: 35.9939,\
    eval_loss: 1.4284523725509644,\
    eval_rouge1: 46.5613,\
    eval_rouge2: 23.6137,\
    eval_rougeL: 37.2397,\
    eval_rougeLsum: 42.7126,\
    eval_samples_per_second: 4.302
    
## Example

    from transformers import PegasusForConditionalGeneration, PegasusTokenizer
    
    model_name = "jpcorb20/pegasus-large-reddit_tifu-samsum-256"
    
    tokenizer = PegasusTokenizer.from_pretrained(model_name)
    model = PegasusForConditionalGeneration.from_pretrained(model_name)
    
    src_text = """Carter: Hey Alexis, I just wanted to let you know that I had a really nice time with you tonight.\r\nAlexis: Thanks Carter. Yeah, I really enjoyed myself as well.\r\nCarter: If you are up for it, I would really like to see you again soon.\r\nAlexis: Thanks Carter, I'm flattered. But I have a really busy week coming up.\r\nCarter: Yeah, no worries. I totally understand. But if you ever want to go grab dinner again, just let me know.\r\nAlexis: Yeah of course. Thanks again for tonight. Carter: Sure. Have a great night.\r\n"""
    
    token_params = dict(max_length=256, truncation=True, padding='longest', return_tensors="pt")
    batch = tokenizer(src_text, **token_params)
    
    translated = model.generate(**batch)
    
    decode_params = dict(num_beams=5, min_length=16, max_length=128, length_penalty=2)
    tgt_text = tokenizer.batch_decode(translated, skip_special_tokens=True, **decode_params)
    
    print(tgt_text)