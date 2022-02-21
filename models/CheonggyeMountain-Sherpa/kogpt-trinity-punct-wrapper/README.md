---
language:
- ko
tags:
- gpt2
license: cc-by-nc-sa-4.0
---

## Model based on
[Ko-GPT-Trinity 1.2B (v0.5)](https://huggingface.co/skt/ko-gpt-trinity-1.2B-v0.5)

## Example
```python
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM 

tokenizer = AutoTokenizer.from_pretrained(
    "CheonggyeMountain-Sherpa/kogpt-trinity-punct-wrapper",
    revision="punct_wrapper-related_words-overfit",  # or punct_wrapper-related_words-minevalloss
    bos_token="<s>",
    eos_token="</s>",
    unk_token="<unk>",
    pad_token="<pad>",
    mask_token="<mask>",
)
model = AutoModelForCausalLM.from_pretrained(
    "CheonggyeMountain-Sherpa/kogpt-trinity-punct-wrapper",
    revision="punct_wrapper-related_words-overfit",  # or punct_wrapper-related_words-minevalloss
    pad_token_id=tokenizer.eos_token_id,
).to(device="cuda")
model.eval()

prompt = "석양이 보이는 경치"
wrapped_prompt = f"@{prompt}@<usr>\n"
with torch.no_grad():
    tokens = tokenizer.encode(wrapped_prompt, return_tensors="pt").to(device="cuda")
    gen_tokens = model.generate(
        tokens,
        max_length=64,
        repetition_penalty=2.0,
        pad_token_id=tokenizer.pad_token_id,
        eos_token_id=tokenizer.eos_token_id,
        bos_token_id=tokenizer.bos_token_id,
        top_k=16,
        top_p=0.8,
    )
    generated = tokenizer.decode(gen_tokens[0][len(tokens[0]):])
 
print(generated)
# 해가 지고 있을 무렵
# 나는 석양을 보러 간다
# 붉은 하늘과 하얀 구름이 나를 반겨줄 것 같아서리
# 하지만 내가 본 해는 저물어만 가고
# 구름마저 자취를 감춘 어둠만이 남아있을 뿐이네
# 내가 탄 배는 보이지도 않고
```