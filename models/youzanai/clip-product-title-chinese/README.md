<!--
 * @Description: 
 * @Version: 
 * @Author: Hardy
 * @Date: 2022-02-09 15:13:53
 * @LastEditors: Hardy
 * @LastEditTime: 2022-02-09 16:59:01
-->

<br />
<p align="center">
  <h1 align="center">clip-product-title-chinese</h1>
</p>

## 基于有赞商品图片和标题语料训练的clip模型。


## Usage
使用模型前，请 git clone https://github.com/youzanai/trexpark.git


```python
import torch
from src.clip.clip import ClipProcesserChinese, ClipChineseModel
import requests
from PIL import Image

clip_processor = ClipProcesserChinese.from_pretrained('youzanai/clip-product-title-chinese')
model = ClipChineseModel.from_pretrained('youzanai/clip-product-title-chinese')

url = 'http://img.yzcdn.cn/upload_files/2015/04/21/0140dac4657f874f2acff9294b28088c.jpg'
img = Image.open(requests.get(url, stream=True).raw).convert('RGB')
imgs = [img]
texts = ['运动鞋', '红色连衣裙', '黑色连衣裙', '大衣', '文具']

f = clip_processor(texts, imgs, return_tensors='pt', truncation=True, padding=True)
del f['token_type_ids']
with torch.no_grad():
    out = model(**f)
logits_per_image, logits_per_text = out['logits_per_image'], out['logits_per_text']

print(logits_per_image.softmax(dim=-1).cpu().detach().numpy())

# 结果： [[1.1700666e-07 9.9948394e-01 5.1582896e-04 4.7687358e-11 6.9604440e-08]]
```


