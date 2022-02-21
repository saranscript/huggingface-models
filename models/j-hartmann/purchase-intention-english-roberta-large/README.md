---
language: "en"
tags:
- roberta
- sentiment
- twitter

widget:
- text: "This looks tasty. Where can I buy it??"
- text: "Now I want this, too."
- text: "You look great today!"
- text: "I just love spring and sunshine!"

---

This RoBERTa-based model can classify *expressed purchase intentions* in English language text in 2 classes:

- purchase intention 🤩
- no purchase intention 😐

The model was fine-tuned on 2,000 manually annotated social media posts. 
The hold-out accuracy is 95% (vs. a balanced 50% random-chance baseline). 
For details on the training approach see Web Appendix F in Hartmann et al. (2021). 

# Application

```python
from transformers import pipeline
classifier = pipeline("text-classification", model="j-hartmann/purchase-intention-english-roberta-large", return_all_scores=True)
classifier("I want this!")
```

```python
Output:
[[{'label': 'no', 'score': 0.0014553926885128021},
  {'label': 'yes', 'score': 0.9985445737838745}]]
```

# Reference
Please cite [this paper](https://journals.sagepub.com/doi/full/10.1177/00222437211037258) when you use our model. Feel free to reach out to [j.p.hartmann@rug.nl](mailto:j.p.hartmann@rug.nl) with any questions or feedback you may have.
```
@article{hartmann2021,
  title={The Power of Brand Selfies},
  author={Hartmann, Jochen and Heitmann, Mark and Schamp, Christina and Netzer, Oded},
  journal={Journal of Marketing Research}
  year={2021}
}
```