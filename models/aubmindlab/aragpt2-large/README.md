---
language: ar
datasets:
 - wikipedia
 - OSIAN
 - 1.5B Arabic Corpus
 - OSCAR Arabic Unshuffled
inference: false
widget:
 - text: "يحكى أن مزارعا مخادعا قام ببيع بئر الماء الموجود في أرضه لجاره مقابل مبلغ كبير من المال"
 - text: "القدس مدينة تاريخية، بناها الكنعانيون في"
 - text: "كان يا ما كان في قديم الزمان"
---

# Arabic GPT2

<img src="https://raw.githubusercontent.com/aub-mind/arabert/master/AraGPT2.png" width="100" align="left"/>

You can find more information in our paper [AraGPT2](https://arxiv.org/abs/2012.15520)

The code in this repository was used to train all GPT2 variants. The code support training and fine-tuning GPT2 on GPUs and TPUs via the TPUEstimator API.

GPT2-base and medium uses the code from the `gpt2` folder and can trains models from the [minimaxir/gpt-2-simple](https://github.com/minimaxir/gpt-2-simple) repository.
These models were trained using the `lamb` optimizer and follow the same architecture as `gpt2` and are fully compatible with the `transformers` library.

GPT2-large and GPT2-mega were trained using the [imcaspar/gpt2-ml](https://github.com/imcaspar/gpt2-ml/) library, and follow the `grover` architecture. You can use the pytorch classes found in `grover/modeling_gpt2.py` as a direct replacement for classes in the `transformers` library (it should support version `v4.x` from `transformers`).
Both models are trained using the `adafactor` optimizer, since the `adam` and `lamb` optimizer use too much memory causing the model to not even fit 1 batch on a TPU core.

AraGPT2 is trained on the same large Arabic Dataset as AraBERTv2.

# Usage

## Testing the model using `transformers`:

```python
from transformers import GPT2TokenizerFast, pipeline
#for base and medium
from transformers import GPT2LMHeadModel
#for large and mega
from arabert.aragpt2.grover.modeling_gpt2 import GPT2LMHeadModel

from arabert.preprocess import ArabertPreprocessor

MODEL_NAME='aubmindlab/aragpt2-large'
arabert_prep = ArabertPreprocessor(model_name=MODEL_NAME)

text=""
text_clean = arabert_prep.preprocess(text)

model = GPT2LMHeadModel.from_pretrained(MODEL_NAME)
tokenizer = GPT2TokenizerFast.from_pretrained(MODEL_NAME)
generation_pipeline = pipeline("text-generation",model=model,tokenizer=tokenizer)

#feel free to try different decodinn settings
generation_pipeline(text,
    pad_token_id=tokenizer.eos_token_id,
    num_beams=10,
    max_length=200,
    top_p=0.9,
    repetition_penalty = 3.0,
    no_repeat_ngram_size = 3)[0]['generated_text']
>>>
```
## Finetunning using `transformers`:

Follow the guide linked [here](https://towardsdatascience.com/fine-tuning-gpt2-on-colab-gpu-for-free-340468c92ed)

## Finetuning using our code with TF 1.15.4:

Create the Training TFRecords:
```bash
python create_pretraining_data.py
 --input_file=<RAW TEXT FILE with documents/article sperated by an empty line>
 --output_file=<OUTPUT TFRecord>
 --tokenizer_dir=<Directory with the GPT2 Tokenizer files>
 ```

 Finetuning:
 ```bash
 python3 run_pretraining.py \\\r\n --input_file="gs://<GS_BUCKET>/pretraining_data/*" \\\r\n --output_dir="gs://<GS_BUCKET>/pretraining_model/" \\\r\n --config_file="config/small_hparams.json" \\\r\n --batch_size=128 \\\r\n --eval_batch_size=8 \\\r\n --num_train_steps= \\\r\n --num_warmup_steps= \\\r\n --learning_rate= \\\r\n --save_checkpoints_steps= \\\r\n --max_seq_length=1024 \\\r\n --max_eval_steps= \\\r\n --optimizer="lamb" \\\r\n --iterations_per_loop=5000 \\\r\n --keep_checkpoint_max=10 \\\r\n --use_tpu=True \\\r\n --tpu_name=<TPU NAME> \\\r\n --do_train=True \\\r\n --do_eval=False
 ```
# Model Sizes

Model | Optimizer | Context size | Embedding Size | Num of heads | Num of layers | Model Size / Num of Params |
 ---|:---:|:---:|:---:|:---:|:---:|:---:
AraGPT2-base | `lamb` | 1024 | 768 | 12 | 12 | 527MB/135M |
AraGPT2-medium | `lamb` | 1024 | 1024 | 16 | 24 |1.38G/370M |
AraGPT2-large | `adafactor` | 1024 | 1280 | 20 | 36 | 2.98GB/792M |
AraGPT2-mega | `adafactor` | 1024 | 1536 | 25 | 48 | 5.5GB/1.46B |

All models are available in the `HuggingFace` model page under the [aubmindlab](https://huggingface.co/aubmindlab/) name. Checkpoints are available in PyTorch, TF2 and TF1 formats.

## Compute

For Dataset Source see the [Dataset Section](#Dataset)

Model | Hardware | num of examples (seq len = 1024) | Batch Size | Num of Steps | Time (in days)
 ---|:---:|:---:|:---:|:---:|:---:
AraGPT2-base | TPUv3-128 | 9.7M | 1792 | 125K | 1.5
AraGPT2-medium | TPUv3-8 | 9.7M | 1152 | 85K | 1.5
AraGPT2-large | TPUv3-128 | 9.7M | 256 | 220k | 3
AraGPT2-mega | TPUv3-128 | 9.7M | 256 | 780K | 9

# Dataset

The pretraining data used for the new AraBERT model is also used for **GPT2 and ELECTRA**.

The dataset consists of 77GB or 200,095,961 lines or 8,655,948,860 words or 82,232,988,358 chars (before applying Farasa Segmentation)

For the new dataset we added the unshuffled OSCAR corpus, after we thoroughly filter it, to the previous dataset used in AraBERTv1 but with out the websites that we previously crawled:
- OSCAR unshuffled and filtered.
- [Arabic Wikipedia dump](https://archive.org/details/arwiki-20190201) from 2020/09/01
- [The 1.5B words Arabic Corpus](https://www.semanticscholar.org/paper/1.5-billion-words-Arabic-Corpus-El-Khair/f3eeef4afb81223df96575adadf808fe7fe440b4)
- [The OSIAN Corpus](https://www.aclweb.org/anthology/W19-4619)
- Assafir news articles. Huge thank you for Assafir for giving us the data

# Disclaimer

 The text generated by GPT2 Arabic is automatically generated by a neural network model trained on a large amount of texts, which does not represent the authors' or their institutes' official attitudes and preferences. The text generated by GPT2 Arabic should only be used for research and scientific purposes. If it infringes on your rights and interests or violates social morality, please do not propagate it.

# If you used this model please cite us as :

```
@inproceedings{antoun-etal-2021-aragpt2,
    title = "{A}ra{GPT}2: Pre-Trained Transformer for {A}rabic Language Generation",
    author = "Antoun, Wissam  and
      Baly, Fady  and
      Hajj, Hazem",
    booktitle = "Proceedings of the Sixth Arabic Natural Language Processing Workshop",
    month = apr,
    year = "2021",
    address = "Kyiv, Ukraine (Virtual)",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2021.wanlp-1.21",
    pages = "196--207",
}
```

# Acknowledgments
Thanks to TensorFlow Research Cloud (TFRC) for the free access to Cloud TPUs, couldn't have done it without this program, and to the [AUB MIND Lab](https://sites.aub.edu.lb/mindlab/) Members for the continuous support. Also thanks to [Yakshof](https://www.yakshof.com/#/) and Assafir for data and storage access. Another thanks for Habib Rahal (https://www.behance.net/rahalhabib), for putting a face to AraBERT.

# Contacts
**Wissam Antoun**: [Linkedin](https://www.linkedin.com/in/wissam-antoun-622142b4/) | [Twitter](https://twitter.com/wissam_antoun) | [Github](https://github.com/WissamAntoun) | <wfa07@mail.aub.edu> | <wissam.antoun@gmail.com>

**Fady Baly**: [Linkedin](https://www.linkedin.com/in/fadybaly/) | [Twitter](https://twitter.com/fadybaly) | [Github](https://github.com/fadybaly) | <fgb06@mail.aub.edu> | <baly.fady@gmail.com>

