# ruclip-vit-large-patch14-224

**RuCLIP** (**Ru**ssian **C**ontrastive **L**anguage–**I**mage **P**retraining) is a multimodal model 
for obtaining images and text similarities and rearranging captions and pictures. 
RuCLIP builds on a large body of work on zero-shot transfer, computer vision, natural language processing and 
multimodal learning. 

Model was trained by [Sber AI](https://github.com/sberbank-ai) and [SberDevices](https://sberdevices.ru/) teams.  
* Task: `text ranking`; `image ranking`; `zero-shot image classification`;
* Type: `encoder`
* Num Parameters: `430M`
* Training Data Volume: `240 million text-image pairs`
* Language: `Russian`
* Context Length: `77`
* Transformer Layers: `12`
* Transformer Width: `768`
* Transformer Heads: `12`
* Image Size: `224`
* Vision Layers: `24`
* Vision Width: `1024`
* Vision Patch Size: `14`

## Usage [Github](https://github.com/sberbank-ai/ru-clip)

```
pip install ruclip
```

```python
clip, processor = ruclip.load("ruclip-vit-large-patch14-224", device="cuda")
```

## Performance
We have evaluated the performance on the following datasets:

| Dataset       | Metric Name    | Metric Result       |
|:--------------|:---------------|:--------------------|
| Food101       | acc            | 0.597		      	   |
| CIFAR10       | acc            | 0.878	             |
| CIFAR100      | acc            | 0.511               |
| Birdsnap      | acc            | 0.172               |
| SUN397        | acc            | 0.484               |
| Stanford Cars | acc            | 0.559               |
| DTD           | acc            | 0.370	             |
| MNIST         | acc            | 0.337	             |
| STL10         | acc            | 0.934	             |
| PCam          | acc            | 0.520               |
| CLEVR         | acc            | 0.152               |
| Rendered SST2 | acc            | 0.529               |
| ImageNet      | acc            | 0.426               |
| FGVC Aircraft | mean-per-class | 0.046               |
| Oxford Pets   | mean-per-class | 0.604               |
| Caltech101    | mean-per-class | 0.777               |
| Flowers102    | mean-per-class | 0.455               |
| HatefulMemes  | roc-auc        | 0.530               |


# Authors

+ Alex Shonenkov: [Github](https://github.com/shonenkov), [Kaggle GM](https://www.kaggle.com/shonenkov)
+ Daniil Chesakov: [Github](https://github.com/Danyache)
+ Denis Dimitrov: [Github](https://github.com/denndimitrov)
+ Igor Pavlov: [Github](https://github.com/boomb0om)
