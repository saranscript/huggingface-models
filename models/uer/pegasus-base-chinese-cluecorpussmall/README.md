---
language: Chinese
datasets: CLUECorpusSmall
widget: 
- text: "内容丰富、版式设计考究、图片华丽、印制精美。[MASK]纸箱内还放了充气袋用于保护。"


---

# Chinese Pegasus

## Model description

This model is pre-trained by [UER-py](https://arxiv.org/abs/1909.05658).

## How to use

You can use this model directly with a pipeline for text2text generation :

```python
>>> from transformers import BertTokenizer, PegasusForConditionalGeneration, Text2TextGenerationPipeline
>>> tokenizer = BertTokenizer.from_pretrained("uer/pegasus-base-chinese-cluecorpussmall")
>>> model = PegasusForConditionalGeneration.from_pretrained("uer/pegasus-base-chinese-cluecorpussmall")
>>> text2text_generator = Text2TextGenerationPipeline(model, tokenizer)  
>>> text2text_generator("内容丰富、版式设计考究、图片华丽、印制精美。[MASK]纸箱内还放了充气袋用于保护。", max_length=50, do_sample=False)
    [{'generated_text': '书 的 质 量 很 好 。'}]
```

## Training data

[CLUECorpusSmall](https://github.com/CLUEbenchmark/CLUECorpus2020/) is used as training data. 

## Training procedure

The model is pre-trained by [UER-py](https://github.com/dbiir/UER-py/) on [Tencent Cloud](https://cloud.tencent.com/). We pre-train 1,000,000 steps with a sequence length of 512.


```
python3 preprocess.py --corpus_path corpora/cluecorpussmall.txt \
                      --vocab_path models/google_zh_vocab.txt \
                      --dataset_path cluecorpussmall_pegasus_seq512_dataset.pt \
                      --processes_num 32 --seq_length 512 \
                      --target gsg --sentence_selection_strategy random
```

```
python3 pretrain.py --dataset_path cluecorpussmall_pegasus_seq512_dataset.pt \
                    --vocab_path models/google_zh_vocab.txt \
                    --config_path models/pegasus/base_config.json \
                    --output_model_path models/cluecorpussmall_pegasus_base_seq512_model.bin \
                    --world_size 8 --gpu_ranks 0 1 2 3 4 5 6 7 \
                    --total_steps 1000000 --save_checkpoint_steps 100000 --report_steps 50000 \
                    --learning_rate 1e-4 --batch_size 8 \
                    --embedding word_sinusoidalpos --remove_embedding_layernorm --tgt_embedding word_sinusoidalpos \
                    --encoder transformer --mask fully_visible --layernorm_positioning pre --decoder transformer \
                    --target gsg --tie_weights --has_lmtarget_bias
```

Finally, we convert the pre-trained model into Huggingface's format:

```
python3 scripts/convert_pegasus_from_uer_to_huggingface.py --input_model_path cluecorpussmall_pegasus_base_seq512_model.bin-250000 \                                                                
                                                           --output_model_path pytorch_model.bin \                                                                                            
                                                           --layers_num 12
```


### BibTeX entry and citation info

```
@inproceedings{zhang2020pegasus,
  title={Pegasus: Pre-training with extracted gap-sentences for abstractive summarization},
  author={Zhang, Jingqing and Zhao, Yao and Saleh, Mohammad and Liu, Peter},
  booktitle={International Conference on Machine Learning},
  pages={11328--11339},
  year={2020},
  organization={PMLR}
}

@article{zhao2019uer,
  title={UER: An Open-Source Toolkit for Pre-training Models},
  author={Zhao, Zhe and Chen, Hui and Zhang, Jinbin and Zhao, Xin and Liu, Tao and Lu, Wei and Chen, Xi and Deng, Haotang and Ju, Qi and Du, Xiaoyong},
  journal={EMNLP-IJCNLP 2019},
  pages={241},
  year={2019}
}
```