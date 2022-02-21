# bengali-t5-base

**bengali-t5-base** is a model trained on the Bengali portion of MT5 dataset. We used the `T5-base` model for this model.

[Flax/Jax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104), organized by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.

The model is trained on around ~11B tokens (64 size batch, 512 tokens, 350k steps). 

## load tokenizer

```
>>> tokenizer = transformers.AutoTokenizer.from_pretrained("flax-community/bengali-t5-base")
>>> tokenizer.encode("আমি বাংলার গান গাই")
>>> tokenizer.decode([93, 1912, 814, 5995, 3, 1])
```

```
[93, 1912, 814, 5995, 3, 1]
'আমি বাংলার গান গাই </s>'
```

## load model

```
>>> config  = T5Config.from_pretrained("flax-community/bengali-t5-base")
>>> model = FlaxT5ForConditionalGeneration.from_pretrained("flax-community/bengali-t5-base", config=config)
```

The model is trained on `de-noising` objectives followed by the script [here](https://huggingface.co/flax-community/bengali-t5-base/blob/main/run_t5_mlm_flax.py) and [here](https://huggingface.co/flax-community/bengali-t5-base/blob/main/run.sh). Currently This model doesn't have any generation capability. If you want this model to have generation capability, please do a finetuning on `prefix-LM` objective mentioned in the [paper](https://arxiv.org/abs/1910.10683). 

See the tensorboard log in `Training metrics` tab.

Please note that we haven't finetuned the model in any downstream task. 

## Proposal
- [Project Proposal](https://discuss.huggingface.co/t/pretrain-t5-from-scratch-in-bengali/7121)

## Participants
- [Ibraheem Muhammad Moosa](https://huggingface.co/ibraheemmoosa)
- [Tasnim Mohiuddin](https://huggingface.co/tasnim)
- [Khalid Saifullah](https://huggingface.co/khalidsaifullaah)
- [Tahsin Mayeesha](https://tahsin-mayeesha.github.io/)
- [M Saiful Bari](https://huggingface.co/sbmaruf)

## Useful links
- [Community Week timeline](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104#summary-timeline-calendar-6)
- [Community Week README](https://github.com/huggingface/transformers/blob/master/examples/research_projects/jax-projects/README.md)
- [Masked Language Modelling example scripts](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling)
- [Model Repository](https://huggingface.co/flax-community/roberta-base-als-demo)
