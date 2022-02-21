```python
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM

# device setting
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
# load model and tokenizer
model_name_or_path = "ddobokki/gpt2_poem"

tokenizer = AutoTokenizer.from_pretrained(model_name_or_path)
model = AutoModelForCausalLM.from_pretrained(model_name_or_path)
model.to(device)

keyword_start_token = "<k>"
keyword_end_token = "</k>"
text = "산 꼭대기가 보이는 경치"
input_text = keyword_start_token + text + keyword_end_token

input_ids = tokenizer.encode(input_text, return_tensors="pt").to(device)
gen_ids = model.generate(
    input_ids, max_length=64, num_beams=100, no_repeat_ngram_size=2
)
generated = tokenizer.decode(gen_ids[0, :].tolist(), skip_special_tokens=True)
>> 오르락내리락
산 꼭대기를 올려다보니
아득히 멀고 아득한
나뭇가지에 매달린
작은 산새 한 마리
이름 모를 풀 한포기 안고
어디론가 훌쩍 떠나가 버렸다
```