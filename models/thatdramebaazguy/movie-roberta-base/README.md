---
datasets:
- imdb
- cornell_movie_dialogue 

language: 
- English

thumbnail: 

tags:
- roberta
- roberta-base
- masked-language-modeling 
- masked-lm

license: cc-by-4.0

---
# roberta-base for MLM 

```
model_name = "thatdramebaazguy/movie-roberta-base"
pipeline(model=model_name, tokenizer=model_name, revision="v1.0", task="Fill-Mask")
```
## Overview
**Language model:** roberta-base  
**Language:** English  
**Downstream-task:** Fill-Mask  
**Training data:** imdb, polarity movie data, cornell_movie_dialogue, 25mlens movie names  
**Eval data:** imdb, polarity movie data, cornell_movie_dialogue, 25mlens movie names    
**Infrastructure**: 4x Tesla v100   
**Code:**  See [example](https://github.com/adityaarunsinghal/Domain-Adaptation/blob/master/scripts/shell_scripts/train_movie_roberta.sh)    

## Hyperparameters
```
Num examples = 4767233
Num Epochs = 2
Instantaneous batch size per device = 20
Total train batch size (w. parallel, distributed & accumulation) = 80
Gradient Accumulation steps = 1
Total optimization steps = 119182
eval_loss  = 1.6153
eval_samples = 20573
perplexity = 5.0296
learning_rate=5e-05
n_gpu = 4

``` 
## Performance

perplexity = 5.0296

Some of my work: 
- [Domain-Adaptation Project](https://github.com/adityaarunsinghal/Domain-Adaptation/)

---
