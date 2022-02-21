---
language: hi
---

# Releasing Hindi ELECTRA model

This is a first attempt at a Hindi language model trained with Google Research's [ELECTRA](https://github.com/google-research/electra).

**Consider using this newer, larger model: https://huggingface.co/monsoon-nlp/hindi-tpu-electra**

<a href="https://colab.research.google.com/drive/1R8TciRSM7BONJRBc9CBZbzOmz39FTLl_">Tokenization and training CoLab</a>

I originally used <a href="https://github.com/monsoonNLP/transformers">a modified ELECTRA</a> for finetuning, but now use SimpleTransformers.

<a href="https://medium.com/@mapmeld/teaching-hindi-to-electra-b11084baab81">Blog post</a> - I was greatly influenced by: https://huggingface.co/blog/how-to-train

## Example Notebooks

This small model has comparable results to Multilingual BERT on <a href="https://colab.research.google.com/drive/18FQxp9QGOORhMENafQilEmeAo88pqVtP">BBC Hindi news classification</a>
and on <a href="https://colab.research.google.com/drive/1UYn5Th8u7xISnPUBf72at1IZIm3LEDWN">Hindi movie reviews / sentiment analysis</a> (using SimpleTransformers)

You can get higher accuracy using ktrain by adjusting learning rate (also: changing model_type in config.json - this is an open issue with ktrain): https://colab.research.google.com/drive/1mSeeSfVSOT7e-dVhPlmSsQRvpn6xC05w?usp=sharing

Question-answering on MLQA dataset: https://colab.research.google.com/drive/1i6fidh2tItf_-IDkljMuaIGmEU6HT2Ar#scrollTo=IcFoAHgKCUiQ

A larger model (<a href="https://huggingface.co/monsoon-nlp/hindi-tpu-electra">Hindi-TPU-Electra</a>) using ELECTRA base size outperforms both models on Hindi movie reviews / sentiment analysis, but
does not perform as well on the BBC news classification task.

## Corpus

Download: https://drive.google.com/drive/folders/1SXzisKq33wuqrwbfp428xeu_hDxXVUUu?usp=sharing

The corpus is two files:
- Hindi CommonCrawl deduped by OSCAR https://traces1.inria.fr/oscar/
- latest Hindi Wikipedia ( https://dumps.wikimedia.org/hiwiki/ ) + WikiExtractor to txt

Bonus notes:
- Adding English wiki text or parallel corpus could help with cross-lingual tasks and training

## Vocabulary

https://drive.google.com/file/d/1-6tXrii3tVxjkbrpSJE9MOG_HhbvP66V/view?usp=sharing

Bonus notes:
- Created with HuggingFace Tokenizers; you can increase vocabulary size and re-train; remember to change ELECTRA vocab_size

## Training

Structure your files, with data-dir named "trainer" here

```
trainer
- vocab.txt
- pretrain_tfrecords
-- (all .tfrecord... files)
- models
-- modelname
--- checkpoint
--- graph.pbtxt
--- model.*
```

CoLab notebook gives examples of GPU vs. TPU setup

[configure_pretraining.py](https://github.com/google-research/electra/blob/master/configure_pretraining.py)

## Conversion

Use this process to convert an in-progress or completed ELECTRA checkpoint to a Transformers-ready model:

```
git clone https://github.com/huggingface/transformers
python ./transformers/src/transformers/convert_electra_original_tf_checkpoint_to_pytorch.py
  --tf_checkpoint_path=./models/checkpointdir
  --config_file=config.json
  --pytorch_dump_path=pytorch_model.bin
  --discriminator_or_generator=discriminator
python
```

```
from transformers import TFElectraForPreTraining
model = TFElectraForPreTraining.from_pretrained("./dir_with_pytorch", from_pt=True)
model.save_pretrained("tf")
```

Once you have formed one directory with config.json, pytorch_model.bin, tf_model.h5, special_tokens_map.json, tokenizer_config.json, and vocab.txt on the same level, run:

```
transformers-cli upload directory
```
