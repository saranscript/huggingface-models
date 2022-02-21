---
language: zh 
widget:
- text: "[CLS]国 色 天 香 ， 姹 紫 嫣 红 ， 碧 水 青 云 欣 共 赏 -"

---

# Chinese Couplet GPT2 Model

## Model description

The model is used to generate Chinese couplets. You can download the model either from the [GPT2-Chinese Github page](https://github.com/Morizeyao/GPT2-Chinese), or via HuggingFace from the link [gpt2-chinese-couplet][couplet].

Since the parameter skip_special_tokens is used in the pipelines.py, special tokens such as [SEP], [UNK] will be deleted, the output results of Hosted inference API (right) may not be properly displayed..

## How to use

You can use the model directly with a pipeline for text generation:

When the parameter skip_special_tokens is True:

```python
>>> from transformers import BertTokenizer, GPT2LMHeadModel, TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/gpt2-chinese-couplet")
>>> model = GPT2LMHeadModel.from_pretrained("uer/gpt2-chinese-couplet")
>>> text_generator = TextGenerationPipeline(model, tokenizer)   
>>> text_generator("[CLS]丹 枫 江 冷 人 初 去 -", max_length=25, do_sample=True)
    [{'generated_text': '[CLS]丹 枫 江 冷 人 初 去 - 黄 叶 声 从 天 外 来 阅 旗'}]
```

When the parameter skip_special_tokens is False:

```python
>>> from transformers import BertTokenizer, GPT2LMHeadModel, TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/gpt2-chinese-couplet")
>>> model = GPT2LMHeadModel.from_pretrained("uer/gpt2-chinese-couplet")
>>> text_generator = TextGenerationPipeline(model, tokenizer)   
>>> text_generator("[CLS]丹 枫 江 冷 人 初 去 -", max_length=25, do_sample=True)
    [{'generated_text': '[CLS]丹 枫 江 冷 人 初 去 - 黄 叶 声 我 酒 不 辞 [SEP] [SEP] [SEP] [SEP] [SEP] [SEP] [SEP] [SEP] [SEP]'}]
```

## Training data

Training data contains 700,000 Chinese couplets which are collected by [couplet-clean-dataset](https://github.com/v-zich/couplet-clean-dataset).

## Training procedure

The model is pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 25,000 steps with a sequence length of 64.

```
python3 preprocess.py --corpus_path corpora/couplet.txt \
                      --vocab_path models/google_zh_vocab.txt \
                      --dataset_path couplet_dataset.pt --processes_num 16 \
                      --seq_length 64 --target lm 
```

```
python3 pretrain.py --dataset_path couplet_dataset.pt \
                    --vocab_path models/google_zh_vocab.txt \
                    --config_path models/gpt2/config.json \
                    --output_model_path models/couplet_gpt2_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 25000 --save_checkpoint_steps 5000 --report_steps 1000 \
                    --learning_rate 5e-4 --batch_size 64 \
                    --embedding word_pos --remove_embedding_layernorm \
                    --encoder transformer --mask causal --layernorm_positioning pre \
                    --target lm --tie_weights
```

Finally, we convert the pre-trained model into Huggingface's format:
```
python3 scripts/convert_gpt2_from_uer_to_huggingface.py --input_model_path couplet_gpt2_model.bin-25000 \
                                                        --output_model_path pytorch_model.bin \
                                                        --layers_num 12
```

### BibTeX entry and citation info

```
@article{radford2019language,
  title={Language Models are Unsupervised Multitask Learners},
  author={Radford, Alec and Wu, Jeff and Child, Rewon and Luan, David and Amodei, Dario and Sutskever, Ilya},
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

[couplet]: https://huggingface.co/uer/gpt2-chinese-couplet