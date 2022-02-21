## Usage
Please use BertTokenizerFast as tokenizer instead of AutoTokenizer.

請使用 BertTokenizerFast 而非 AutoTokenizer。
```
from transformers import (
  BertTokenizerFast,
  AutoModelForCausalLM,
)

tokenizer = BertTokenizerFast.from_pretrained('p208p2002/gpt2-drcd-qg-hl')
model = AutoModelForCausalLM.from_pretrained('p208p2002/gpt2-drcd-qg-hl')
```
### Input Format
```
C' = [c1, c2, ..., [HL], a1, ..., a|A|, [HL], ..., c|C|]
```
### Input Example
```
哈利·波特是英國作家[HL]羅琳[HL]撰寫的七部幻想小說系列。
```
> 誰撰寫哈利·波特?