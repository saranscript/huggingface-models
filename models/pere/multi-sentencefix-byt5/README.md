---
license: cc
---
# Multi-Lingual DeUnCaser - Base byT5 Version
The output from Automated Speak Recognition software is usually uncased and without any punctation. This does not make a very readable text.

The DeUnCaser is a sequence-to-sequence model that is reversing this process. It adds punctation, and capitalises the correct words. In some languages this means adding capital letters at start of sentences and on all proper nouns, in other languages, like German, it means capitalising the first letter of all nouns. It will also make attempts at adding hyphens and parentheses if this is making the meaning clearer.

It is using based on the multi-lingual T5 model. It is finetuned for 100,000 steps. The finetuning scripts is based on 100,000 training examples from each of the 44 languages with Latin alphabet that is both part of OSCAR and the mT5 training set: Afrikaans, Albanian, Basque, Catalan, Cebuano, Czech, Danish, Dutch, English, Esperanto, Estonian, Finnish, French, Galician, German, Haitian Creole, Hungarian, Icelandic, Indonesian, Irish, Italian, Kurdish, Latin, Latvian, Lithuanian, Luxembourgish, Malagasy, Malay, Maltese, Norwegian Bokmål, Norwegian Nynorsk, Polish, Portuguese, Romanian, Slovak, Spanish, Sundanese, Swahili, Swedish, Turkish, Uzbek, Vietnamese, Welsh, West Frisian.

A Notebook for creating the training corpus is available [here](https://colab.research.google.com/drive/1bkH94z-0wIQP8Pz0qXFndhoQsokU-78x?usp=sharing).





