---
language: multilingual
thumbnail: https://doesnotexist.codes/messlab.png
tags:
- programming
- gpt2
- causal-lm
license: cc0-1.0
---

# GPT-CSRC

This is a GPT2 774M model trained on the C/C++ code of the top 10,000 most popular packages in Debian, according to the [Debian Popularity Contest](https://popcon.debian.org/). The source files were deduplicated using a process similar to the OpenWebText preprocessing (basically a locality-sensitive hash to detect near-duplicates). The model was originally trained using [NVIDIA's Megatron-LM](https://github.com/nvidia/Megatron-LM) but has been converted to Huggingface. Note that the tokenizer is *not* the standard GPT2 BPE vocab, but one that has been trained for this dataset; the tokenizer is also available from this repository.

The processed dataset (in JSON format) can be found here: [csrc\_dataset\_large.json.gz](https://moyix.net/~moyix/csrc_dataset_large.json.gz).

This model was used to generate snippets for the web site [This Code Does Not Exist](https://doesnotexist.codes/).

# Usage

```
>>> import torch
>>> from transformers import AutoModelForCausalLM, AutoTokenizer
>>> model = AutoModelForCausalLM.from_pretrained("moyix/csrc_774m")
>>> device = torch.device("cuda")
>>> model.to(device)
>>> tokenizer = AutoTokenizer.from_pretrained("moyix/csrc_774m")
>>> prompt = tokenizer.encode('// say hello\nvoid hello() {', return_tensors="pt")
>>> output = model.generate(input_ids=prompt.to(device), max_length=32, num_return_sequences=1, do_sample=True, num_beams=4)
>>> print(tokenizer.decode(output[0].tolist(),clean_up_tokenization_spaces=True))
// say hello
void hello() {
  std::cout << "hello" << std::endl;
}

int main() {

```