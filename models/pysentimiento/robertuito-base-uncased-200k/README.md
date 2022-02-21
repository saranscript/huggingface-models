# robertuito-base-uncased

**WORK IN PROGRESS**

RoBERTa model trained on tweets. 

For the time being, please use [this function](https://github.com/finiteautomata/finetune_vs_scratch/blob/main/finetune_vs_scratch/preprocessing.py#L13) before feeding it to the model. We still need to create a proper tokenizer for this model



## Masked LM

To test the masked LM, take into account that space is encoded inside SentencePiece's tokens. So, if you want to test

```
Este es un día<mask>
```

don't put a space between `día` and `<mask>`