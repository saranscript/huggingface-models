## ParsTwiNER: Transformer-based Model for Named Entity Recognition at Informal Persian
An open, broad-coverage corpus and model for informal Persian named entity recognition collected from Twitter. 
Paper presenting ParsTwiNER: [2021.wnut-1.16](https://aclanthology.org/2021.wnut-1.16/)
---
## Results
The following table summarizes the F1 score on our corpus obtained by ParsTwiNER as compared to ParsBERT as a SoTA for Persian NER.
### Named Entity Recognition on Our Corpus
| Entity Type | ParsTwiNER F1 |  ParsBert F1   |
|:-----------:|:-------------:|:--------------:|
|  PER        |     91        |      80        |
|  LOC        |     82        |      68        |
|  ORG        |     69        |      55        |
|  EVE        |     41        |      12        |
|  POG        |     85        |      -         |
|  NAT        |     82.3      |      -         |
|  Total      |     81.5      |      69.5      |

## How to use
### TensorFlow 2.0
```python
from transformers import TFAutoModelForTokenClassification
tokenizer = AutoTokenizer.from_pretrained("overfit/twiner-bert-base-mtl")
model = TFAutoModelForTokenClassification.from_pretrained("overfit/twiner-bert-base-mtl")
twiner_mtl = pipeline('ner', model=model, tokenizer=tokenizer, ignore_labels=[])
```
## Cite 
Please cite the following paper in your publication if you are using [ParsTwiNER](https://aclanthology.org/2021.wnut-1.16/) in your research:
```markdown
@inproceedings{aghajani-etal-2021-parstwiner,
    title = "{P}ars{T}wi{NER}: A Corpus for Named Entity Recognition at Informal {P}ersian",
    author = "Aghajani, MohammadMahdi  and
      Badri, AliAkbar  and
      Beigy, Hamid",
    booktitle = "Proceedings of the Seventh Workshop on Noisy User-generated Text (W-NUT 2021)",
    month = nov,
    year = "2021",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.wnut-1.16",
    pages = "131--136",
    abstract = "As a result of unstructured sentences and some misspellings and errors, finding named entities in a noisy environment such as social media takes much more effort. ParsTwiNER contains about 250k tokens, based on standard instructions like MUC-6 or CoNLL 2003, gathered from Persian Twitter. Using Cohen{'}s Kappa coefficient, the consistency of annotators is 0.95, a high score. In this study, we demonstrate that some state-of-the-art models degrade on these corpora, and trained a new model using parallel transfer learning based on the BERT architecture. Experimental results show that the model works well in informal Persian as well as in formal Persian.",
}
```
## Acknowledgments
The authors would like to thank Dr. Momtazi for her support. Furthermore, we would like to acknowledge the accompaniment provided by Mohammad Mahdi Samiei and Abbas Maazallahi.
## Contributors
- Mohammad Mahdi Aghajani: [Linkedin](https://www.linkedin.com/in/mohammadmahdi-aghajani-821843147/), [Github](https://github.com/mmaghajani)
- Ali Akbar Badri:  [Linkedin](https://www.linkedin.com/in/aliakbarbadri/), [Github](https://github.com/AliAkbarBadri)
- Dr. Hamid Beigy:  [Linkedin](https://www.linkedin.com/in/hamid-beigy-8982604b/)
- Overfit Team: [Github](https://github.com/overfit-ir), [Telegram](https://t.me/nlp_stuff)

## Releases
### Release v1.0.0 (Aug 01, 2021)
This is the first version of our ParsTwiNER.