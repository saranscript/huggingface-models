---
language: Chinese
datasets: CLUECorpusSmall
widget: 
- text: "作为电子[MASK]的平台，京东绝对是领先者。如今的刘强[MASK]已经是身价过[MASK]的老板。"


---

# Chinese BART

## Model description

This model is pre-trained by [UER-py](https://arxiv.org/abs/1909.05658).

## How to use

You can use this model directly with a pipeline for text2text generation :

```python
>>> from transformers import BertTokenizer, BartForConditionalGeneration, Text2TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/bart-chinese-4-768-cluecorpussmall")
>>> model = BartForConditionalGeneration.from_pretrained("uer/bart-chinese-4-768-cluecorpussmall")
>>> text2text_generator = Text2TextGenerationPipeline(model, tokenizer)  
>>> text2text_generator("中国的首都是[MASK]京", max_length=50, do_sample=False)
    [{'generated_text': '中 国 的 首 都 是 北 京'}]
```

## Training data

[CLUECorpusSmall](https://github.com/CLUEbenchmark/CLUECorpus2020/) Common Crawl and some short messages are used as training data. 

## Training procedure

The model is pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 1,000,000 steps with a sequence length of 512.


we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_bart_from_uer_to_huggingface.py --input_model_path cluecorpussmall_bart_medium_seq512_model.bin-250000 \                                                                
                                                        --output_model_path pytorch_model.bin \                                                                                            
                                                        --layers_num 4
```


### BibTeX entry and citation info

```
@article{lewis2019bart,
  title={Bart: Denoising sequence-to-sequence pre-training for natural language generation, translation, and comprehension},
  author={Lewis, Mike and Liu, Yinhan and Goyal, Naman and Ghazvininejad, Marjan and Mohamed, Abdelrahman and Levy, Omer and Stoyanov, Ves and Zettlemoyer, Luke},
  journal={arXiv preprint arXiv:1910.13461},
  year={2019}
}

@article{zhao2019uer,
  title={UER: An Open-Source Toolkit for Pre-training Models},
  author={Zhao, Zhe and Chen, Hui and Zhang, Jinbin and Zhao, Xin and Liu, Tao and Lu, Wei and Chen, Xi and Deng, Haotang and Ju, Qi and Du, Xiaoyong},
  journal={EMNLP-IJCNLP 2019},
  pages={241},
  year={2019}
}
```