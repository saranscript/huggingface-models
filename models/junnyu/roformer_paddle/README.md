# paddle paddle版本的RoFormer

# 需要安装最新的paddlenlp
`pip install git+https://github.com/PaddlePaddle/PaddleNLP.git`

## 预训练模型转换

预训练模型可以从 huggingface/transformers 转换而来，方法如下（适用于roformer模型，其他模型按情况调整）：

1. 从huggingface.co获取roformer模型权重
2. 设置参数运行convert.py代码
3. 例子：
   假设我想转换https://huggingface.co/junnyu/roformer_chinese_base 权重
   - (1)首先下载 https://huggingface.co/junnyu/roformer_chinese_base/tree/main 中的pytorch_model.bin文件,假设我们存入了`./roformer_chinese_base/pytorch_model.bin`
   - (2)运行convert.py
        ```bash
        python convert.py \
            --pytorch_checkpoint_path ./roformer_chinese_base/pytorch_model.bin \
            --paddle_dump_path ./roformer_chinese_base/model_state.pdparams
        ```
   - (3)最终我们得到了转化好的权重`./roformer_chinese_base/model_state.pdparams`
   
 
## 预训练MLM测试
### test_mlm.py
```python
import paddle
import argparse
from paddlenlp.transformers import RoFormerForPretraining, RoFormerTokenizer

def test_mlm(text, model_name):
    model = RoFormerForPretraining.from_pretrained(model_name)
    model.eval()
    tokenizer = RoFormerTokenizer.from_pretrained(model_name)
    tokens = ["[CLS]"]
    text_list = text.split("[MASK]")
    for i,t in enumerate(text_list):
        tokens.extend(tokenizer.tokenize(t))
        if i==len(text_list)-1:
            tokens.extend(["[SEP]"])
        else:
            tokens.extend(["[MASK]"])

    input_ids_list = tokenizer.convert_tokens_to_ids(tokens)
    input_ids = paddle.to_tensor([input_ids_list])

    with paddle.no_grad():
        pd_outputs = model(input_ids)[0][0]
    pd_outputs_sentence = "paddle: "
    for i, id in enumerate(input_ids_list):
        if id == tokenizer.convert_tokens_to_ids(["[MASK]"])[0]:
            tokens = tokenizer.convert_ids_to_tokens(pd_outputs[i].topk(5)[1].tolist())
            pd_outputs_sentence += "[" + "||".join(tokens) + "]"
        else:
            pd_outputs_sentence += "".join(
                tokenizer.convert_ids_to_tokens([id], skip_special_tokens=True)
            )
    print(pd_outputs_sentence)

if __name__ == "__main__":
    parser = argparse.ArgumentParser()
    parser.add_argument(
        "--model_name", default="roformer-chinese-base", type=str, help="Pretrained roformer name or path."
    )
    parser.add_argument(
        "--text", default="今天[MASK]很好，我想去公园玩！", type=str, help="MLM text."
    )
    args = parser.parse_args()
    test_mlm(text=args.text, model_name=args.model_name)

```
### 输出
```bash
python test_mlm.py --model_name roformer-chinese-base --text 今天[MASK]很好，我想去公园玩！
# paddle: 今天[天气||天||阳光||太阳||空气]很好，我想去公园玩！
python test_mlm.py --model_name roformer-chinese-base --text 北京是[MASK]的首都！
# paddle: 北京是[中国||谁||中华人民共和国||我们||中华民族]的首都！
python test_mlm.py --model_name roformer-chinese-char-base --text 今天[MASK]很好，我想去公园玩！
# paddle: 今天[天||气||都||风||人]很好，我想去公园玩！
python test_mlm.py --model_name roformer-chinese-char-base --text 北京是[MASK]的首都！
# paddle: 北京是[谁||我||你||他||国]的首都！
```