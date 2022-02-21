# 使用

这个模型是在uer/bart-chinese-6-960-cluecorpussmall基础上训练的，数据量不是很大，但是修改了默认分词。

使用pkuseg分词，禁用BertTokenizer的do_basic_tokenize分词，不禁用do_basic_tokenize的话会把正常词汇按照逐字分词，禁用后可以导入自己的分词方案。

pip install git+https://github.com/napoler/tkit-AutoTokenizerPosition
```python
import pkuseg
from tkitAutoTokenizerPosition.AutoPos import AutoPos
seg = pkuseg.pkuseg(model_name='medicine')  # 程序会自动下载所对应的细领域模型
tokenizer = BertTokenizer.from_pretrained("uer/chinese_roberta_L-2_H-128",do_basic_tokenize=False)

ATP=AutoPos(seg,tokenizer)
# 清理文本中的问题
ATP.getTokenize(text)


```
分词结果如下
```
['他', '##们', '的', '伤', '##害', ',', '以', '##及', '陷', '##阱', '能', '##力', '的', '组', '##合', ',', '猎', '##人', '对', '##于', '任', '##何', '团', '##队', '都', '是', '最', '##好', '的', '拉', '##怪', '##者', '.'], 'cut': ['他们', '的', '伤害', ',', '以及', '陷阱', '能力', '的', '组合', ',', '猎人', '对于', '任何', '团队', '都', '是', '最好', '的', '拉怪者', '.']
```

https://www.kaggle.com/terrychanorg/napolerbartchinese6960wordspkuseg



https://www.kaggle.com/terrychanorg/buliddataforbert-7803feff2

https://www.kaggle.com/terrychanorg/bart-notebook8wewew6eeb0f8af
https://www.kaggle.com/terrychanorg/fork-of-bart-notebook8wewew6eeb0f8af/data?scriptVersionId=77962540
