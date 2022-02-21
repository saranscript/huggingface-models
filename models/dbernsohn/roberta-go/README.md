# roberta-go
---
language: Go
datasets:
- code_search_net
---

This is a [roberta](https://arxiv.org/pdf/1907.11692.pdf) pre-trained version on the [CodeSearchNet dataset](https://github.com/github/CodeSearchNet) for **Golang** Mask Language Model mission.

To load the model:
(necessary packages: !pip install transformers sentencepiece)
```python
from transformers import AutoTokenizer, AutoModelWithLMHead, pipeline
tokenizer = AutoTokenizer.from_pretrained("dbernsohn/roberta-go")
model = AutoModelWithLMHead.from_pretrained("dbernsohn/roberta-go")

fill_mask = pipeline(
    "fill-mask",
    model=model,
    tokenizer=tokenizer
)
```

You can then use this model to fill masked words in a Java code.

```python
code = """
package main

import (
	"fmt"
	"runtime"
)

func main() {
	fmt.Print("Go runs on ")
	switch os := runtime.<mask>; os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		// freebsd, openbsd,
		// plan9, windows...
		fmt.Printf("%s.\n", os)
	}
}
""".lstrip()

pred = {x["token_str"].replace("Ġ", ""): x["score"] for x in fill_mask(code)}
sorted(pred.items(), key=lambda kv: kv[1], reverse=True)
[('GOOS', 0.11810332536697388),
 ('FileInfo', 0.04276798665523529),
 ('Stdout', 0.03572738170623779),
 ('Getenv', 0.025064032524824142),
 ('FileMode', 0.01462600938975811)]
```

The whole training process and hyperparameters are in my [GitHub repo](https://github.com/DorBernsohn/CodeLM/tree/main/CodeMLM)

> Created by [Dor Bernsohn](https://www.linkedin.com/in/dor-bernsohn-70b2b1146/)