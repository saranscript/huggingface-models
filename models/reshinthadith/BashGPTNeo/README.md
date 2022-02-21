---
language: 
  - English
  - Bash
thumbnail: "Neural Program Synthesis for Bash"
tags:
- code-representation-learning
- program-synthesis
datasets:
- nlc2cmd
metrics:
- metric1
- metric2

---
# BashGPT-Neo

## What is it ?
BashGPT-Neo is a [Neural Program Synthesis](https://www.microsoft.com/en-us/research/project/neural-program-synthesis/) Model for Bash Commands and Shell Scripts. Trained on the data provided by [NLC2CMD](https://nlc2cmd.us-east.mybluemix.net/). It is fine-tuned version of GPTNeo-125M by EleutherAI.

## Usage
```py
from transformers import AutoTokenizer, AutoModelForCausalLM
tokenizer = AutoTokenizer.from_pretrained("reshinthadith/BashGPTNeo")
model = AutoModelForCausalLM.from_pretrained("reshinthadith/BashGPTNeo")
```

## Core Contributors 👥 
- [Reshinth Adithyan](https://github.com/reshinthadithyan)
- [Aditya Thuruvas](https://github.com/dhuruvasaditya)