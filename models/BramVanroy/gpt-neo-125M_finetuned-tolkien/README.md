---
language: 
- en
---

*First attempt. Likely poor quality!*

Finetuned version of GPT-Neo 125M on some of Tolkien's works, namely Beren and Lúthien, The Lord of The Rings (+ appendices), and The Hobbit. 

Trained with a strided sliding window. Paragraphs were separated by new lines.

- batch size: 32
- train epochs: 10
- context window size: 128
- input chunk size: 2048
- current revision: chkpt 6300
