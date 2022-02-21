 # IndT5: A Text-to-Text Transformer for 10 Indigenous Languages
 &nbsp;
<img src="https://huggingface.co/UBC-NLP/IndT5/raw/main/IND_langs_large7.png" alt="drawing" width="45%" height="45%" align="right"/>
In this work,  we introduce IndT5, the  first  Transformer  language  model  for  Indigenous languages.  To train IndT5, we build IndCorpu,  a  new  corpus  for 10 Indigenous languages  and  Spanish. 

&nbsp;

# IndT5

We train an Indigenous language model adopting the unified and flexible
text-to-text transfer Transformer (T5) approach. T5 treats every
text-based language task as a “text-to-text" problem, taking text format
as input and producing new text format as output. T5 is essentially an
encoder-decoder Transformer, with the encoder and decoder similar in
configuration and size to a BERT<sub>Base</sub> but with some
architectural modifications. Modifications include applying a
normalization layer before a sub-block and adding a pre-norm (i.e.,
initial input to the sub-block output).

# IndCourpus

We build IndCorpus, a collection of 10 Indigeous languages and Spanish comprising 1.17GB of text, from both Wikipedia and the Bible.

### Data size and number of sentences in monolingual dataset (collected from Wikipedia and Bible)
| **Target Language** | **Wiki Size (MB)**        | **Wiki #Sentences**           | **Bible Size (MB)**  | **Bible #Sentences**|
|-------------------|------------------|-------------------|------------------------|-|
|Hñähñu                   | -                |    -                             | 1.4     |    7.5K                                          |
|Wixarika                 | -            |       -                             |  1.3   |   7.5K|
|Nahuatl                  | 5.8           |    61.1K                         | 1.5  |      7.5K|
|Guarani                  | 3.7            |      28.2K                           | 1.3 |      7.5K                                              |
|Bribri                   | -               |    -                             | 1.5  |        7.5K                                        |
|Rarámuri                 | -                |     -                            | 1.9  |         7.5K                                       |
|Quechua                  | 5.9               |     97.3K                        | 4.9   |    31.1K                                            |
|Aymara                   | 1.7                |     32.9K                         | 5   | 30.7K|
|Shipibo-Konibo           | -                   |     -                         | 1    |    7.9K                                             |
|Asháninka                | -                    |     -                       | 1.4    |   7.8K                                          |
|Spanish                      | 1.13K             |    5M    | -              | - |
|Total | 1.15K  |  5.22M   |    19.8 |     125.3K|
# Github
More details about our model can be found here: https://github.com/UBC-NLP/IndT5




# BibTex

```bibtex
@inproceedings{nagoudi-etal-2021-indt5,
    title = "{I}nd{T}5: A Text-to-Text Transformer for 10 Indigenous Languages",
    author = "Nagoudi, El Moatez Billah  and Chen, Wei-Rui  and Abdul-Mageed, Muhammad  and Cavusoglu, Hasan",
    booktitle = "Proceedings of the First Workshop on Natural Language Processing for Indigenous Languages of the Americas",
    month = jun,
    year = "2021",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.americasnlp-1.30",
    doi = "10.18653/v1/2021.americasnlp-1.30",
    pages = "265--271"
}
```
    
 