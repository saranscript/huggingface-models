# ChineseBERT-base

This repository contains code, model, dataset for **ChineseBERT** at ACL2021.

paper:  
**[ChineseBERT: Chinese Pretraining Enhanced by Glyph and Pinyin Information](https://arxiv.org/abs/2106.16038)**  
*Zijun Sun, Xiaoya Li, Xiaofei Sun, Yuxian Meng, Xiang Ao, Qing He, Fei Wu and Jiwei Li*

code:   
[ChineseBERT github link](https://github.com/ShannonAI/ChineseBert)

## Model description
We propose ChineseBERT, which incorporates both the glyph and pinyin information of Chinese
characters into language model pretraining.  
 
First, for each Chinese character, we get three kind of embedding.
 - **Char Embedding:** the same as origin BERT token embedding.
 - **Glyph Embedding:** capture visual features based on different fonts of a Chinese character.
 - **Pinyin Embedding:** capture phonetic feature from the pinyin sequence ot a Chinese Character.
 
Then, char embedding, glyph embedding and pinyin embedding 
are first concatenated, and mapped to a D-dimensional embedding through a fully 
connected layer to form the fusion embedding.   
Finally, the fusion embedding is added with the position embedding, which is fed as input to the BERT model.  
The following image shows an overview architecture of ChineseBERT model.
 
![MODEL](https://raw.githubusercontent.com/ShannonAI/ChineseBert/main/images/ChineseBERT.png)

ChineseBERT leverages the glyph and pinyin information of Chinese 
characters to enhance the model's ability of capturing
context semantics from surface character forms and
disambiguating polyphonic characters in Chinese.