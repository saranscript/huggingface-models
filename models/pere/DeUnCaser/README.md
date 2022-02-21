---
language: no
tags:
- translation
widget:
- text: "moscow says deployments in eastern europe increase tensions nato says russia has moved troops to belarus"
- text: "dette er en liten test som er laget av per egil kummervold han er en forsker som tidligere jobbet ved nasjonalbiblioteket"
- text: "tirsdag var travel for ukrainas president volodymyr zelenskyj på morgenen tok han imot polens statsminister mateusz morawiecki"
license: cc-by-4.0
---

# DeUnCaser
The output from Automated Speak Recognition software is usually uncased and without any punctation. This does not make a very readable text. 

The DeUnCaser is a sequence-to-sequence byT5 model that is reversing this process. It adds punctation, and capitalises the correct words. In some languages this means adding capital letters at start of sentences and on all proper nouns, in other languages, like German, it means capitalising the first letter of all nouns. It will also make attempts at adding hyphens and parentheses if this is making the meaning clearer.

It is using based on the multi-lingual base model. However the current finetuning is only done on Norwegian. For other languages this will be mainly experimental. I will update it with support for other languages if there is any demand.

