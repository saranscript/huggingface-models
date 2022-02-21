---
language: zh
widget: 
- text: "著名诗歌《假如生活欺骗了你》的作者是"
  context: "普希金从那里学习人民的语言，吸取了许多有益的养料，这一切对普希金后来的创作产生了很大的影响。这两年里，普希金创作了不少优秀的作品，如《囚徒》、《致大海》、《致凯恩》和《假如生活欺骗了你》等几十首抒情诗，叙事诗《努林伯爵》，历史剧《鲍里斯·戈都诺夫》，以及《叶甫盖尼·奥涅金》前六章。"

---

# Chinese RoBERTa-Base Model for QA

## Model description

The model is used for extractive question answering. You can download the model from the link [roberta-base-chinese-extractive-qa](https://huggingface.co/uer/roberta-base-chinese-extractive-qa).

## How to use

You can use the model directly with a pipeline for extractive question answering:

```python
>>> from transformers import AutoModelForQuestionAnswering,AutoTokenizer,pipeline
>>> model = AutoModelForQuestionAnswering.from_pretrained('uer/roberta-base-chinese-extractive-qa')
>>> tokenizer = AutoTokenizer.from_pretrained('uer/roberta-base-chinese-extractive-qa')
>>> QA = pipeline('question-answering', model=model, tokenizer=tokenizer)
>>> QA_input = {'question': "著名诗歌《假如生活欺骗了你》的作者是",'context': "普希金从那里学习人民的语言，吸取了许多有益的养料，这一切对普希金后来的创作产生了很大的影响。这两年里，普希金创作了不少优秀的作品，如《囚徒》、《致大海》、《致凯恩》和《假如生活欺骗了你》等几十首抒情诗，叙事诗《努林伯爵》，历史剧《鲍里斯·戈都诺夫》，以及《叶甫盖尼·奥涅金》前六章。"}
>>> QA(QA_input)
    {'score': 0.9766426682472229, 'start': 0, 'end': 3, 'answer': '普希金'}
```

## Training data

Training data comes from three sources: [cmrc2018](https://github.com/ymcui/cmrc2018), [webqa](https://spaces.ac.cn/archives/4338), and [laisi](https://www.kesci.com/home/competition/5d142d8cbb14e6002c04e14a/content/0). We only use the train set of three datasets.

## Training procedure

The model is fine-tuned by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud TI-ONE](https://cloud.tencent.com/product/tione/). We fine-tune three epochs with a sequence length of 512 on the basis of the pre-trained model [chinese_roberta_L-12_H-768](https://huggingface.co/uer/chinese_roberta_L-12_H-768). At the end of each epoch, the model is saved when the best performance on development set is achieved.

```
python3 run_cmrc.py --pretrained_model_path models/cluecorpussmall_roberta_base_seq512_model.bin-250000 \
                    --vocab_path models/google_zh_vocab.txt \
                    --train_path extractive_qa.json \
                    --dev_path datasets/cmrc2018/dev.json \
                    --output_model_path models/extractive_qa_model.bin \
                    --learning_rate 3e-5 --batch_size 32 --epochs_num 3 --seq_length 512 \
                    --embedding word_pos_seg --encoder transformer --mask fully_visible
```

Finally, we convert the fine-tuned model into Huggingface's format:

```
python3 scripts/convert_bert_extractive_qa_from_uer_to_huggingface.py --input_model_path extractive_qa_model.bin \
                                                                         --output_model_path pytorch_model.bin \
                                                                         --layers_num 12
```

### BibTeX entry and citation info

```
@article{zhao2019uer,
  title={UER: An Open-Source Toolkit for Pre-training Models},
  author={Zhao, Zhe and Chen, Hui and Zhang, Jinbin and Zhao, Xin and Liu, Tao and Lu, Wei and Chen, Xi and Deng, Haotang and Ju, Qi and Du, Xiaoyong},
  journal={EMNLP-IJCNLP 2019},
  pages={241},
  year={2019}
}
```