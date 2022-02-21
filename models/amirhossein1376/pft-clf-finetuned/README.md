---
license: apache-2.0
language: fa
widget:
 - text: "امروز دربی دو تیم پرسپولیس و استقلال در ورزشگاه آزادی تهران برگزار می‌شود."
 - text: "وزیر امور خارجه اردن تاکید کرد که همه کشورهای عربی خواهان روابط خوب با ایران هستند.

به گزارش ایسنا به نقل از شبکه فرانس ۲۴، ایمن الصفدی معاون نخست‌وزیر و وزیر امور خارجه اردن پس از کنفرانس لیبی در پاریس در گفت‌وگویی با فرانس ۲۴ تاکید کرد: موضع اردن روشن است، ما خواستار روابط منطقه‌ای مبتنی بر حسن همجواری و عدم مداخله در امور داخلی هستیم. بسیاری از مسائل و مشکلات منطقه نیاز به رسیدگی از طریق گفت‌وگو دارد.


الصفدی هرگونه گفت‌وگوی با واسطه اردن با ایران را رد کرده و گفت: ما با نمایندگان هیچ‌کس صحبت نمی‌کنیم و زمانی که با ایران صحبت می‌کنیم مستقیماً با دولت این کشور بوده و از طریق تماس تلفنی وزیر امور خارجه دو کشور.

وی تاکید کرد: همه در منطقه عربی خواستار روابط خوب با ایران هستند، اما برای تحقق این امر باید روابط بر اساس شفافیت و بر اساس اصول احترام به همسایگی و عدم مداخله در امور داخلی باشد.
"
tags:
- generated_from_trainer
metrics:
- matthews_correlation
model-index:
- name: pft-clf-finetuned
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pft-clf-finetuned

This model is a fine-tuned version of [HooshvareLab/bert-fa-zwnj-base](https://huggingface.co/HooshvareLab/bert-fa-zwnj-base) on an "FarsNews1398" dataset. This dataset contains a collection of news that has been gathered from the farsnews website which is a news agency in Iran. You can download the dataset from [here](https://www.kaggle.com/amirhossein76/farsnews1398). I used category, abstract, and paragraphs of news for doing text classification. "abstract" and "paragraphs" for each news concatenated together and "category" used as a target for classification.

The notebook used for fine-tuning can be found [here](https://colab.research.google.com/drive/1jC2dfKRASxCY-b6bJSPkhEJfQkOA30O0?usp=sharing). I've reported loss and Matthews correlation criteria on the validation set.

It achieves the following results on the evaluation set:
- Loss: 0.0617
- Matthews Correlation: 0.9830

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 6
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Matthews Correlation |
|:-------------:|:-----:|:-----:|:---------------:|:--------------------:|
| 0.0634        | 1.0   | 20276 | 0.0617          | 0.9830               |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
