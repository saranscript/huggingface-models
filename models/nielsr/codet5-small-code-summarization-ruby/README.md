---
license: apache-2.0
tags:
- codet5
datasets:
- code_x_glue_ct_code_to_text
widget:
- text: 'def pad(tensor, paddings, mode: "CONSTANT", name: nil) _op(:pad, tensor, paddings, mode: mode, name: name) end </s>'
---

# Description

CodeT5-small model, fine-tuned on the code summarization subtask of CodeXGLUE (Ruby programming language). This model can generate a docstring of a given function written in Ruby.

# Notebook

The notebook that I used to fine-tune CodeT5 can be found [here](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/T5/Fine_tune_CodeT5_for_generating_docstrings_from_Ruby_code.ipynb).

# Usage

Here's how to use this model: 

```python
from transformers import RobertaTokenizer, T5ForConditionalGeneration

model_name = "nielsr/codet5-small-code-summarization-ruby"
tokenizer = RobertaTokenizer.from_pretrained(model_name)
model = T5ForConditionalGeneration.from_pretrained(model_name)

code = """
def update_with_file_contents(digest, filename)
      File.open(filename) do |io|
        while (chunk = io.read(1024 * 8))
          digest.update(chunk)
        end
      end
    end
"""

input_ids = tokenizer(code, return_tensors="pt").input_ids
outputs = model.generate(input_ids)
print(tokenizer.decode(outputs[0], skip_special_tokens=True))
# Update the digest with the contents of the given file
```