---
language:
- en
tags:
- text aggregation
- summarization
license: apache-2.0
datasets:
- toloka/CrowdSpeech
metrics:
- wer
---

# T5 Large for Text Aggregation

## Model description

This is a T5 Large fine-tuned for crowdsourced text aggregation tasks. The model takes multiple performers' responses and yields a single aggregated response. This approach was introduced for the first time during [VLDB 2021 Crowd Science Challenge](https://crowdscience.ai/challenges/vldb21) and originally implemented at the second-place competitor's [GitHub](https://github.com/A1exRey/VLDB2021_workshop_t5). The [paper](http://ceur-ws.org/Vol-2932/short2.pdf) describing this model was presented at the [2nd Crowd Science Workshop](https://crowdscience.ai/conference_events/vldb21).

## How to use

```python
from transformers import AutoModelForSeq2SeqLM, AutoTokenizer, AutoConfig
mname = "toloka/t5-large-for-text-aggregation"
tokenizer = AutoTokenizer.from_pretrained(mname)
model = AutoModelForSeq2SeqLM.from_pretrained(mname)

input = "samplee text | sampl text | sample textt"
input_ids = tokenizer.encode(input, return_tensors="pt")
outputs = model.generate(input_ids)
decoded = tokenizer.decode(outputs[0], skip_special_tokens=True)
print(decoded)  # sample text
```


## Training data

Pretrained weights were taken from the [original](https://huggingface.co/t5-large) T5 Large model by Google. For more details on the T5 architecture and training procedure see https://arxiv.org/abs/1910.10683

Model was fine-tuned on `train-clean`, `dev-clean` and `dev-other` parts of the [CrowdSpeech](https://huggingface.co/datasets/toloka/CrowdSpeech) dataset that was introduced in [our paper](https://openreview.net/forum?id=3_hgF1NAXU7&referrer=%5BAuthor%20Console%5D(%2Fgroup%3Fid%3DNeurIPS.cc%2F2021%2FTrack%2FDatasets_and_Benchmarks%2FRound1%2FAuthors%23your-submissions).


## Training procedure

The model was fine-tuned for eight epochs directly following the HuggingFace summarization training [example](https://github.com/huggingface/transformers/tree/master/examples/pytorch/summarization).

## Eval results

Dataset    | Split      | WER
-----------|------------|----------
CrowdSpeech| test-clean | 4.99
CrowdSpeech| test-other | 10.61


### BibTeX entry and citation info
```bibtex
@inproceedings{Pletenev:21,
  author    = {Pletenev, Sergey},
  title     = {{Noisy Text Sequences Aggregation as a Summarization Subtask}},
  year      = {2021},
  booktitle = {Proceedings of the 2nd Crowd Science Workshop: Trust, Ethics, and Excellence in Crowdsourced Data Management at Scale},
  pages     = {15--20},
  address   = {Copenhagen, Denmark},
  issn      = {1613-0073},
  url       = {http://ceur-ws.org/Vol-2932/short2.pdf},
  language  = {english},
}
```

```bibtex
@misc{pavlichenko2021vox,
      title={Vox Populi, Vox DIY: Benchmark Dataset for Crowdsourced Audio Transcription}, 
      author={Nikita Pavlichenko and Ivan Stelmakh and Dmitry Ustalov},
      year={2021},
      eprint={2107.01091},
      archivePrefix={arXiv},
      primaryClass={cs.SD}
}
```
