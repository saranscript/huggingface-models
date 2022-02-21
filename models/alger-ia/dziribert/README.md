---
language: 
- ar
- dz

tags:
- pytorch
- bert
- multilingual
- ar
- dz

license: apache-2.0

widget:
- text: " أنا من الجزائر من ولاية [MASK] "
- text: "rabi [MASK] khouya sami"
- text: " ربي [MASK] خويا لعزيز"
- text: "tahya el [MASK]."
- text: "rouhi ya dzayer [MASK]"

inference: true
---

<img src="https://raw.githubusercontent.com/alger-ia/dziribert/main/dziribert_drawing.png" alt="drawing" width="25%" height="25%" align="right"/>


# DziriBERT


DziriBERT is the first Transformer-based Language Model that has been pre-trained specifically for the Algerian Dialect. It handles Algerian text contents written using both Arabic and Latin characters. It sets new state of the art results on Algerian text classification datasets, even if it has been pre-trained on much less data (~1 million tweets).

For more information, please visit our paper: https://arxiv.org/pdf/2109.12346.pdf.

## How to use

```python
from transformers import BertTokenizer, BertForMaskedLM

tokenizer = BertTokenizer.from_pretrained("alger-ia/dziribert")
model = BertForMaskedLM.from_pretrained("alger-ia/dziribert")

```

You can find a fine-tuning script in our Github repo: https://github.com/alger-ia/dziribert

### How to cite

```bibtex
@article{dziribert,
  title={DziriBERT: a Pre-trained Language Model for the Algerian Dialect},
  author={Abdaoui, Amine and Berrimi, Mohamed and Oussalah, Mourad and Moussaoui, Abdelouahab},
  journal={arXiv preprint arXiv:2109.12346},
  year={2021}
}
```

## Contact 

Please contact amine.abdaoui@huawei.com for any question, feedback or request.
