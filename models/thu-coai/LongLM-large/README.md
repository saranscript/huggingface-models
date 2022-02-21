---
language:
- zh
thumbnail: http://coai.cs.tsinghua.edu.cn/coai/img/logo.png?v=13923
tags:
- pytorch
- lm-head
- zh
widget:
- text: "小咕噜对靳司寒完全是个自来熟，小家伙爬进他怀里小手搂着他的脖子，奶声奶气的要求：“靳蜀黎,你给咕噜讲故事好不好？”讲故事？童话故事吗？“我不会。”小家伙明显不信。嘟着小嘴大眼汪汪的盯着他，“哼。”小家伙轻轻哼了一声,靳司寒默了半晌，<extra_id_1>"
- text: "美女亲自打招呼，这可是破天荒第一次，之前不管他献多少次殷勤，美女<extra_id_1>甩他，难道今天真是老天<extra_id_2>不敢<extra_id_3>的兄连滚带爬的来到<extra_id_4>身边队友都带着艳<extra_id_5>他，<extra_id_6>连计算机系的那票球友都在那儿不住地偷看MAGGIE，这种感觉真<extra_id_7>毙了！"
inference:
  parameters:
    top_p: 0.9
---
## LongLM

### 1. Parameters

| Versions     | $d_m$ | $d_{ff}$ | $d_{kv}$ | $n_h$ | $n_e/n_d$ | \# P   |
| ------------ | ----- | -------- | -------- | ----- | --------- | ---- |
| LongLM-small | 512   | 2,048    | 64       | 8     | 6/6       | 60M  |
| LongLM-base  | 768   | 3,072    | 64       | 12    | 12/12     | 223M |
| LongLM-large | 1,536 | 3,072    | 64       | 12    | 24/32     | 1B   |

- $d_m$: the dimension of hidden states
- $d_{ff}$: the dimension of feed forward layers
- $d_{kv}$: the dimension of  the keys/values in the self-attention layers
- $n_h$: the number of attention heads
- $n_e$: the number of hidden layers of the encoder
- $n_d$: the number of hidden layers of the decoder
- \#P: the number of parameters

### 2. Pretraining Tasks

Encoder-decoder models are trained typically by maximizing the likelihood of the target output given an input. To improve the capacities of both the encoder and decoder, we propose to train LongLM with two pretraining tasks including text inﬁlling (Raffel et al., 2020) and conditional continuation (Radford et al., 2019). For the ﬁrst task, the input is a text where a number of spans are sampled and replaced by special tokens with unique IDs, while the output is the spans delimited by the special tokens used in the input. The lengths of masked spans are drawn from a Poisson distribution with λ=3 and all masked tokens compress 15% of the original texts. As for the second task, the input and output are respectively the front and back half of a text, which is split into two parts randomly. 

### 3. Pretraining Data

We collect 120G novels as the pretraining data for LongLM. 

### 4. Checkpoints


1. **Model Loading:** 

   ```python\
   from transformers import T5Tokenizer, T5ForConditionalGeneration
   tokenizer = T5Tokenizer.from_pretrained('LongLM-large')
   model = T5ForConditionalGeneration.from_pretrained('LongLM-large')
   ```


2. **Generation:**

   ```python
   input_ids = tokenizer("小咕噜对，<extra_id_1>",return_tensors="pt", padding=True, truncation=True, max_length=512).input_ids.to(device)
   
   gen = model.generate(input_ids, do_sample=True, decoder_start_token_id=1, top_p=0.9, max_length=512)
   ```


### 5. Dependencies

```
datasets                1.6.2
deepspeed               0.3.16
huggingface-hub         0.0.8
jieba                   0.42.1
jsonlines               2.0.0
nltk                    3.5
numpy                   1.19.5
pytorch-lightning       1.2.0
regex                   2020.11.13
rouge                   1.0.1
rouge-score             0.0.4
sacrebleu               1.5.0
scipy                   1.5.4
sentencepiece           0.1.95
tokenizers              0.10.1
torch                   1.8.1
torchaudio              0.8.0
torchmetrics            0.2.0
torchvision             0.9.0
transformers            4.6.1
```

### 6. Contributers

[Jian Guan](https://jianguanthu.github.io/) at [thu-coai](http://coai.cs.tsinghua.edu.cn/)

## Citation

```txt
@misc{guan2021lot,
      title={LOT: A Benchmark for Evaluating Chinese Long Text Understanding and Generation}, 
      author={Jian Guan and Zhuoer Feng and Yamei Chen and Ruilin He and Xiaoxi Mao and Changjie Fan and Minlie Huang},
      year={2021},
      eprint={2108.12960},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```
