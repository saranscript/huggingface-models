# T5

## Overview

The T5 model was presented in [Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer](https://arxiv.org/pdf/1910.10683.pdf) by Colin Raffel, Noam Shazeer, Adam Roberts, Katherine Lee, Sharan Narang, Michael Matena, Yanqi Zhou, Wei Li, Peter J. Liu.

The abstract from the paper is the following:

*Transfer learning, where a model is first pre-trained on a data-rich task before being finetuned on a downstream task, has emerged as a powerful technique in natural language processing (NLP). The effectiveness of transfer learning has given rise to a diversity of approaches, methodology, and practice. In this paper, we explore the landscape of transfer learning techniques for NLP by introducing a unified framework that converts all text-based language problems into a text-to-text format. Our systematic study compares pre-training objectives, architectures, unlabeled data sets, transfer approaches, and other factors on dozens of language understanding tasks. By combining the insights from our exploration with scale and our new “Colossal Clean Crawled Corpus”, we achieve state-of-the-art results on many benchmarks covering summarization, question answering, text classification, and more. To facilitate future work on transfer learning for NLP, we release our data set, pre-trained models, and code.*

This model was contributed by [stevekola](https://huggingface.co/stevekola). The original code can be found [here](https://github.com/google-research/text-to-text-transfer-transformer).

**Pretraining Dataset:** [C4](https://www.tensorflow.org/datasets/catalog/c4)

## Usage Example

```
from huggingface_hub import snapshot_download
import tensorflow_text
import tensorflow as tf
import os

CACHE_DIR = "hfhub_cache"
os.mkdir(CACHE_DIR)

snapshot_download(repo_id="stevekola/T5", cache_dir=CACHE_DIR)

saved_model_path = os.path.join(CACHE_DIR, os.listdir(CACHE_DIR)[0])
model = tf.saved_model.load(saved_model_path, ["serve"])

def predict_fn(x):
 return model.signatures['serving_default'](tf.constant(x))['outputs'].numpy()

def answer(question):
  return predict_fn([question])[0].decode('utf-8')
  
for question in [
  "translate English to French: where do we go from here",
  "translate English to German: where do we go from here",
  "translate English to Romanian: where do we go from here",
  "cola sentence: where do we go from here",
  "stsb sentence1: I'm overjoyed about today's event. sentence2: I'm so happy today",
  "summarize: Nigeria is losing about 6 billion to 9 billion yearly to the non-passage of the bill, which would have given legal teeth to the water sub-sector for optimal performance like other sectors.",
]:
    print(answer(question))
```

## Test it Out

You can test the [Gradio](https://huggingface.co/spaces/stevekola/T5-multitasks-gradio/) and [Streamlit](https://huggingface.co/spaces/stevekola/T5-multitasks-streamlit) implementations on Spaces!