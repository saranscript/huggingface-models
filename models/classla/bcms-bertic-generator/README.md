---
language: 
- hr
- bs
- sr
- cnr
- hbs

tags:
- masked-lm

widget:
- text: "Zovem se Marko i radim u [MASK]."

license: apache-2.0

---

# BERTić&ast; [bert-ich] /bɜrtitʃ/ - A transformer language model for Bosnian, Croatian, Montenegrin and Serbian

&ast; The name should resemble the facts (1) that the model was trained in Zagreb, Croatia, where diminutives ending in -ić (as in fotić, smajlić, hengić etc.) are very popular, and (2) that most surnames in the countries where these languages are spoken end in -ić (with diminutive etymology as well).

This is the smaller generator of the main [discriminator model](https://huggingface.co/classla/bcms-bertic), useful if you want to continue pre-training the discriminator model.

If you use the model, please cite the following paper:

```
@inproceedings{ljubesic-lauc-2021-bertic,
    title = "{BERT}i{\'c} - The Transformer Language Model for {B}osnian, {C}roatian, {M}ontenegrin and {S}erbian",
    author = "Ljube{\v{s}}i{\'c}, Nikola  and Lauc, Davor",
    booktitle = "Proceedings of the 8th Workshop on Balto-Slavic Natural Language Processing",
    month = apr,
    year = "2021",
    address = "Kiyv, Ukraine",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2021.bsnlp-1.5",
    pages = "37--42",

}
```
