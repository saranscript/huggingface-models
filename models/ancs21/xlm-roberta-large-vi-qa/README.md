---
language: vi
tags:
- vi
- xlm-roberta
widget:
- text: Toà nhà nào cao nhất Việt Nam?
  context: Landmark 81 là một toà nhà chọc trời trong tổ hợp dự án Vinhomes Tân Cảng,
    một dự án có tổng mức đầu tư 40.000 tỷ đồng, do Công ty Cổ phần Đầu tư xây dựng
    Tân Liên Phát thuộc Vingroup làm chủ đầu tư. Toà tháp cao 81 tầng, hiện tại là
    toà nhà cao nhất Việt Nam và là toà nhà cao nhất Đông Nam Á từ tháng 3 năm 2018.

license: mit
metrics:
- f1
- em
---


# XLM-RoBERTa large for QA on Vietnamese languages (also support various languages)

## Overview

- Language model: xlm-roberta-large
- Fine-tune: [deepset/xlm-roberta-large-squad2](https://huggingface.co/deepset/xlm-roberta-large-squad2)
- Language: Vietnamese
- Downstream-task: Extractive QA
- Dataset: [mailong25/bert-vietnamese-question-answering](https://github.com/mailong25/bert-vietnamese-question-answering/tree/master/dataset)
- Training data: train-v2.0.json (SQuAD 2.0 format)
- Eval data: dev-v2.0.json (SQuAD 2.0 format)
- Infrastructure: 1x Tesla P100 (Google Colab)

## Performance

Evaluated on dev-v2.0.json
```
  exact: 136 / 141
  f1: 0.9692671394799054
```

Evaluated on Vietnamese XQuAD: [xquad.vi.json](https://github.com/deepmind/xquad/blob/master/xquad.vi.json)
```
  exact: 604 / 1190
  f1: 0.7224454217571596
 ```

## Author

An Pham (ancs21.ps [at] gmail.com)

## License

MIT