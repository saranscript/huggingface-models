---
language: de
tags:
- grammar
widget:
- text: "correct german grammar: es ist schön so viele tolle menschen um sich zu haben denn ohne sie wäre es nicht so schön"
---

example outputs:

input: ich liebe das leben --> output: Ich liebe das Leben.

input: es ist schön so viele tolle menschen um sich zu haben denn ohne sie wäre es nicht so schön --> output: Es ist schön, so viele tolle Menschen, um sich zu haben, denn ohne sie wäre es nicht so schön.

input: der kunde hat ausdrücklich nach dirk verlangt weil er den rabatt haben möchte --> output: Der Kunde hat ausdrücklich nach Dirk verlangt, weil er den Rabatt haben möchte.


the data can be prepared like this:
the broken_text is used as input, while the text is the output
```python

import re
import phonetics
import random

chars_to_ignore_regex = "[^A-Za-z0-9\ö\ä\ü\Ö\Ä\Ü\ß\-,;.:?! ]+"
broken_chars_to_ignore_regex = "[^A-Za-z0-9\ö\ä\ü\Ö\Ä\Ü\ß\- ]+"


def do_manipulation(string):
    text = re.sub(chars_to_ignore_regex, '', string)
    broken_text = re.sub(broken_chars_to_ignore_regex, "", text.lower())

    if(random.randint(0,100) >= 50):
        for xyz in range(int(len(broken_text.split(" "))/4)):
            if(random.randint(0,100) > 30):
                randc = random.choice(broken_text.split(" "))
                if(random.randint(0,10) > 4):
                    broken_text = broken_text.replace(randc, ''.join(random.choice('abcdefghijklmnopqrstuvxyz') for _ in range(len(randc))).lower())
                else:
                    broken_text = broken_text.replace(randc, phonetics.metaphone(randc).lower())

    return text, broken_text

```
