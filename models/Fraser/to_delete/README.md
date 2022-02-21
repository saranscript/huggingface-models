---
language: 
  - en
thumbnail: "https://huggingface.co/Fraser/program-synthesis/resolve/main/img.png"
tags:
- program-synthesis
license: "mit"
datasets:
- program-synthesis
---
# Program Synthesis Data

Generated program synthesis datasets used to train [dreamcoder](https://github.com/ellisk42/ec).

Currently just supports text & list data.

```python
_FEATURES = datasets.Features(
    {
        "description": datasets.Value("string"),
        "input": datasets.Value("string"),
        "output": datasets.Value("string"),
        "types": datasets.Value("string")
    }
)
```

![](https://huggingface.co/Fraser/program-synthesis/resolve/main/img.png)
