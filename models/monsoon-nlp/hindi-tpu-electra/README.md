---
language: hi
---

# Hindi language model
## Trained with ELECTRA base size settings

<a href="https://colab.research.google.com/drive/1R8TciRSM7BONJRBc9CBZbzOmz39FTLl_">Tokenization and training CoLab</a>

## Example Notebooks

This model outperforms Multilingual BERT on <a href="https://colab.research.google.com/drive/1UYn5Th8u7xISnPUBf72at1IZIm3LEDWN">Hindi movie reviews / sentiment analysis</a> (using SimpleTransformers)

You can get higher accuracy using ktrain + TensorFlow, where you can adjust learning rate and
other hyperparameters: https://colab.research.google.com/drive/1mSeeSfVSOT7e-dVhPlmSsQRvpn6xC05w?usp=sharing

Question-answering on MLQA dataset: https://colab.research.google.com/drive/1i6fidh2tItf_-IDkljMuaIGmEU6HT2Ar#scrollTo=IcFoAHgKCUiQ

A smaller model (<a href="https://huggingface.co/monsoon-nlp/hindi-bert">Hindi-BERT</a>) performs better on a BBC news classification task.

## Corpus

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
