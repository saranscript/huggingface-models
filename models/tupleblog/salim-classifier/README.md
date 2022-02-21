---
widget:
- text: "รัฐรับผิดชอบทุกชีวิตไม่ได้หรอกคนให้บริการต้องจัดการเองถ้าจะเปิดผับบาร์"
---

![Salim Word Cloud](https://raw.githubusercontent.com/tupleblog/salim-classifier/main/images/wordcloud.jpg)

# Salim-Classifier

**วัตถุประสงค์:** ทุกวันนี้หาเพื่อนที่รักชาติ ศาสนา พระมหากษัตริย์ รัฐบาลยากเหลือเกิน มีแต่พวกสามกีบ ควายแดงคอยจ้องจะทำร้าย
ทางทีมของเราจึงสร้างโมเดลมาเพื่อช่วยหาเพื่อนสลิ่มจากคอมเม้น ที่นับวันจะหลงเหลืออยู่น้อยยิ่งนักในสังคมไทย ทั้งนี้เพื่อเป็นแนวทางในการสร้างสังคมสลิ่มที่แข็งแรงต่อไป

## วิธีการใช้งาน

สามารถลง `transfomers` จาก Huggingface และใช้งานโมเดลได้ดังต่อไปนี้

``` py
from transformers import (
    AutoTokenizer,
    AutoModelForSequenceClassification,
    pipeline
)

# download model from hub
tokenizer = AutoTokenizer.from_pretrained("tupleblog/salim-classifier")
model = AutoModelForSequenceClassification.from_pretrained("tupleblog/salim-classifier")

# using pipeline to classify an input text
classifier = pipeline("sentiment-analysis", model=model, tokenizer=tokenizer)
text = "จิตไม่ปกติ วันๆคอยแต่ให้คนเสี้ยมทะเลาะกันด่ากัน คอยจ้องแต่จะเล่นงานรัฐบาล ความคดด้านลบ"
classifier(text)
# >> [{'label': 'HIGHLY LIKELY SALIM', 'score': 0.9989368915557861}] ยินดีด้วย น่าจะเป็นสลิ่ม!
```

## การเก็บข้อมูล

สร้างข้อมูลตัวอย่างและทำการ Annotate จากนั้นนำข้อมูลมาเทรนโมเดลด้วย WangchanBERTa
โดยข้อมูลอาจมีความ bias เนื่องจากทางทีมงานเป็นผู้เก็บข้อมูลเอง

## ทดลองใช้งานผ่าน HuggingFace

ท่านสามารถทดลองใช้งานผ่าน HuggingFace โดยใส่คอมเม้นจาก Facebook เข้าไปในช่องได้ในเว็บไซต์
[huggingface.co/tupleblog/salim-classifier](https://huggingface.co/tupleblog/salim-classifier)

**ตัวอย่างประโยค**
- รัฐรับผิดชอบทุกชีวิตไม่ได้หรอกคนให้บริการต้องจัดการเองถ้าจะเปิดผับบาร์
- แค่เคารพกฎหมาย คนพวกนี้ยังทำไม่ได้เลย แล้วจะถามหาความก้าวหน้าของประเทศ​ ?
- หมามันยังยืนเคารพธงชาติ แต่พวกนี้กลับทำอะไรไม่อายเดรัจฉาน
- ถ้าไม่ชอบประชาธิปไตย จะไปใช้วิธีการปกครองแบบไหนหรอครับ แล้วแบบไหนถึงดีหรอ ผมไม่เข้าใจครับอดีตผ่านไปแล้ว ทำไมไม่มองที่อนาคตกันหละครับ
- อีพวกสามกีบ`<pad>`

สำหรับข้อความที่สั้นกว่า 50 ตัวอักษรแนะนำให้เติม `<pad>` ตามหลังข้อความเพื่อความแม่นยำที่สูงขึ้น

## Performance

We report performance on 20% evaluation set (accuracy, precision, recall, F1-score macro) as follows:

| Accuracy | Precision | Recall |   F1   |
| -------- | --------- | ------ | ------ |
| 86.15%   | 86.12%    | 86.13%  | 86.13% |
