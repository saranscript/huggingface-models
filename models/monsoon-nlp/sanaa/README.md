---
language: ar
---

# Sanaa
## Arabic GPT-2 demo

This is a small GPT-2 model retrained on Arabic Wikipedia circa September 2020
(due to memory limits, the first 600,000 lines of the Wiki dump)

There is NO content filtering in the current version; do not use for public-facing
text generation.

## Training

Training notebook: https://colab.research.google.com/drive/1Z_935vTuZvbseOsExCjSprrqn1MsQT57

Steps to training:
- Follow beginning of Pierre Guillou's Portuguese GPT-2 notebook: https://github.com/piegu/fastai-projects/blob/master/finetuning-English-GPT2-any-language-Portuguese-HuggingFace-fastaiv2.ipynb to download Arabic Wikipedia and run WikiExtractor
- Read Beginner's Guide by Ng Wai Foong https://medium.com/@ngwaifoong92/beginners-guide-to-retrain-gpt-2-117m-to-generate-custom-text-content-8bb5363d8b7f
- Following Ng Wai Foong's instructions, create an encoded .npz corpus (this was very small in my project
   and would be improved by adding many X more training data)
- Run generate_unconditional_samples.py and other sample code to generate text
- Download TensorFlow checkpoints
- Use my notebook code to write vocab.json, empty merge.txt
- Copy config.json from similar GPT-2 arch, edit for changes as needed

```python
am = AutoModel.from_pretrained('./argpt', from_tf=True)
am.save_pretrained("./")
```

## Generating text in SimpleTransformers

Finetuning notebook: https://colab.research.google.com/drive/1fXFH7g4nfbxBo42icI4ZMy-0TAGAxc2i

```python
from simpletransformers.language_generation import LanguageGenerationModel
model = LanguageGenerationModel("gpt2", "monsoon-nlp/sanaa")
model.generate("مدرستي")
```

## Finetuning dialects in SimpleTransformers

I finetuned this model on different Arabic dialects to generate a new
model (monsoon-nlp/sanaa-dialect on HuggingFace) with some additional
control tokens.

Finetuning notebook: https://colab.research.google.com/drive/1fXFH7g4nfbxBo42ic$

```python
from simpletransformers.language_modeling import LanguageModelingModel
ft_model = LanguageModelingModel('gpt2', 'monsoon-nlp/sanaa', args=train_args)
ft_model.tokenizer.add_tokens(["[EGYPTIAN]", "[MSA]", "[LEVANTINE]", "[GULF]"])
ft_model.model.resize_token_embeddings(len(ft_model.tokenizer))
ft_model.train_model("./train.txt", eval_file="./test.txt")

# exported model
from simpletransformers.language_generation import LanguageGenerationModel
model = LanguageGenerationModel("gpt2", "./dialects")
model.generate('[EGYPTIAN]' + "مدرستي")
```
