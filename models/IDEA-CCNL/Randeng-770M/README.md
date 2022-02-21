---
language: 
  - zh
license: apache-2.0

inference: false

---
# Randeng-770M model (Chinese)，one model of [Fengshenbang-LM](https://github.com/IDEA-CCNL/Fengshenbang-LM).
The 770 million parameter Randeng-770M large model, using 280G Chinese data, 16 A100 training for 14 days，which is a standard transformer structure.


## Usage
There is no structure of Randeng-770M in [Transformers](https://github.com/huggingface/transformers), you can run follow code to get structure of Randeng-770M from [Fengshenbang-LM](https://github.com/IDEA-CCNL/Fengshenbang-LM)

 ```shell
 git clone https://github.com/IDEA-CCNL/Fengshenbang-LM.git
 ```

## Usage
```python
from model.megatron_t5.modeling_megatron_t5 import T5ForConditionalGeneration
from model.megatron_t5.configuration_magetron_t5 import T5Config
from model.megatron_t5.tokenization_megatron_t5 import T5Tokenizer

tokenizer = T5Tokenizer.from_pretrained('IDEA-CCNL/Randeng-770M')
config = T5Config.from_pretrained('IDEA-CCNL/Randeng-770M')
model = T5ForConditionalGeneration.from_pretrained('IDEA-CCNL/Randeng-770M')

```

## Citation
If you find the resource is useful, please cite the following website in your paper.
```
@misc{Fengshenbang-LM,
  title={Fengshenbang-LM},
  author={IDEA-CCNL},
  year={2021},
  howpublished={\url{https://github.com/IDEA-CCNL/Fengshenbang-LM}},
}
```