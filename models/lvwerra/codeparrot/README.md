# CodeParrot 🦜

CodeParrot 🦜 is a GPT-2 model (1.5B parameters) trained to generate Python code.

## Usage

You can load the CodeParrot model and tokenizer directly in `transformers`:

```Python
from transformers import AutoTokenizer, AutoModelWithLMHead
  
tokenizer = AutoTokenizer.from_pretrained("lvwerra/codeparrot")
model = AutoModelWithLMHead.from_pretrained("lvwerra/codeparrot")

inputs = tokenizer("def hello_world():", return_tensors="pt")
outputs = model(**inputs)
```

or with a `pipeline`:

```Python
from transformers import pipeline

pipe = pipeline("text-generation", model="lvwerra/codeparrot")
outputs = pipe("def hello_world():")
```

## Training

The model was trained on the cleaned [CodeParrot 🦜 dataset](https://huggingface.co/datasets/lvwerra/codeparrot-clean) with the following settings:

|Config|Value|
|-------|-----|
|Batch size| 512|
|Context size| 1024 |
|Training steps| 50'000|
|Gradient accumulation| 16|
|Gradient checkpointing| True|
|Learning rate| 2e-4 |
|Weight decay | 0.1 |
|Warmup steps| 750 |
|Schedule| Cosine |

The training was executed on 16 x A100 (40GB) GPUs. This setting amounts to roughly 26 billion tokens.

## Performance

We evaluated the model on OpenAI's [HumanEval](https://huggingface.co/datasets/openai_humaneval) benchmark which consists of programming challenges:

| Metric | Value |
|-------|-----|
|pass@1 | 3.58% |
|pass@10 | 8.03% |
|pass@100 | 14.96% |

The [pass@k metric](https://huggingface.co/metrics/code_eval) tells the probability that at least one out of k generations passes the tests. 

## Resources

- Dataset: [full](https://huggingface.co/datasets/lvwerra/codeparrot-clean), [train](https://huggingface.co/datasets/lvwerra/codeparrot-clean-train), [valid](https://huggingface.co/datasets/lvwerra/codeparrot-clean-valid)
- Code: [repository](https://github.com/huggingface/transformers/tree/master/examples/research_projects/codeparrot)
- Spaces: [generation](), [highlighting]()