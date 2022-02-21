---
license: cc-by-4.0
tags:
- generated_from_trainer
language: th
model-index:
- name: thai-bert-multi-cased-finetuned-xquadv1-finetuned-squad
  results: []
widget:
- text: "สราวุธ มาตรทอง เข้าสู่วงการบันเทิงเมื่อปีอะไร"
  context: "สราวุธ มาตรทอง (ชื่อเล่น: อ้น เกิดเมื่อวันที่ 2 ตุลาคม พ.ศ. 2519) เป็นนักแสดงชาวไทย จบการศึกษาจากมหาวิทยาลัยราชภัฏพระนค เข้าสู่วงการบันเทิงเมื่อปี พ.ศ. 2538 จากการ ชักชวนของ กมล ภู่วัฒนวนิชย์ แห่งบริษัทบรอดคาซท์ ไทยเทเลวิชั่น มีผลงานแสดงชิ้นแรกจาก ใส่ไข่ อะไรเอ่ย, 6/16 ร้ายบริสุทธิ์ และมีผลงานสร้างชื่อคือละครเรื่อง ฉลุย และ น้ำใสใจจริง นอกจากนี้ยังได้ทำอัลบั้มประกอบละคร ฉลุย คู่กับ ทีน สราวุฒิ พุ่มทอง มีผลงานภาพยนตร์เรื่อง ความรักครั้งสุดท้าย (2546) เคยได้รับการเสนอชื่อเข้าชิงรางวัลภาพยนตร์ไทย ชมรมวิจารณ์บันเทิง ครั้งที่ 12 สาขานักแสดงสมทบยอดเยี่ยมจากภาพยนตร์เรื่องนี้ และยังมีละครซิตคอมเรื่อง เทวดาสาธุ นอกจากนี้ยังเคยเป็นดีเจให้กับ สถานีวิทยุ เรดิโอโหวต แซตเทิลไลท์ 93.5 MHz และยังเป็นพิธกร รายการเวเอฟเวอร์ ออกอากาศทางช่อง 3 ในวันเสาร์ เวลา 07.55-08.20 น. ในเดือนตุลาคม พ.ศ. 2551 เจ้าตัวได้ยอมรับว่าคลิปหลุดทางอินเทอร์เน็ต ที่มีเพศสัมพันธ์กับหญิงสาวเป็นเจ้าตัวจริง คนที่เอาไปลงน่าจะเป็นคนที่พบโทรศัพท์ของตนเอง" 

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# thai-bert-multi-cased-finetuned-xquadv1-finetuned-squad

This model is a fine-tuned version of [mrm8488/bert-multi-cased-finetuned-xquadv1](https://huggingface.co/mrm8488/bert-multi-cased-finetuned-xquadv1) on Thai dataset from [iApp Technology Co., Ltd.](https://github.com/iapp-technology/iapp-wiki-qa-dataset).

## Intended uses & limitations

This model intends to use with Thai question and answering task

## Training and evaluation data

Trained and evaluated by [iApp Technology Co., Ltd.](https://github.com/iapp-technology/iapp-wiki-qa-dataset) dataset.

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 2
- eval_batch_size: 2
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 4
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2

## Performance
Evaluated on the SQuAD 1.0 test dataset
```
"exact": 57.39972337482711
"f1": 68.10794016188211
"total": 723
```

### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
