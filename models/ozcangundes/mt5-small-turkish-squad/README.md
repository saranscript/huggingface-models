---
language: tr
datasets:
- TQUAD
pipeline_tag: question-answering
license: mit
---

# mT5-small based Turkish Question Answering System

[Google's Multilingual T5-small](https://github.com/google-research/multilingual-t5) is fine-tuned on [Turkish Question Answering dataset](https://github.com/TQuad/turkish-nlp-qa-dataset) for **Q&A** downstream task by using Pytorch Lightning.⚡  

The notebook that includes all fine tuning process will be shared on my Github page later. mT5 small model has 300 million parameters and model size is about 1.2GB. Therefore, it takes significant amount of time to fine tune it.

**Important Note**: mT5 was only pre-trained on [mC4](https://www.tensorflow.org/datasets/catalog/c4#c4multilingual)
excluding any supervised training. Therefore, the mT5 model has to be fine-tuned before it is useable on a downstream task.

## Usage 🚀

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

tokenizer = AutoTokenizer.from_pretrained("ozcangundes/mt5-small-turkish-squad")

model = AutoModelForSeq2SeqLM.from_pretrained("ozcangundes/mt5-small-turkish-squad")

def get_answer(question,context):
  source_encoding=tokenizer(
    question,
    context,
    max_length=512,
    padding="max_length",
    truncation="only_second",
    return_attention_mask=True,
    add_special_tokens=True,
    return_tensors="pt")
  
  generated_ids=model.generate(
      input_ids=source_encoding["input_ids"],
      attention_mask=source_encoding["attention_mask"],
      max_length=120)

  preds=[tokenizer.decode(gen_id, skip_special_tokens=True, clean_up_tokenization_spaces=True) for gen_id in generated_ids]

  return "".join(preds)
```

### Example 1
```python
question={
    "context":"Pardus, Google'ın öğrencilerle staj ve kendini geliştirme imkânı ile \ 
    tasarılara geliştirici ve katkı sağlamayı amaçladığı açık kaynak tasarısı \
    Google Summer of Code'a 2008 ve 2009 olmak üzere iki kere katılmıştır. Bu organizasyona \
    ilk katılan Türk tasarısı Pardus olmuştur. Bazı dönemlerde Pardus hakkındaki gelişmeleri \
    halka duyurmak ve tasarıya olan ilgiyi arttırmak amacıyla CeBIT Eurasia Bilişim Fuarı'na \
    katılım sağlanmaktadır. 2006, 2008, 2009, 2010, 2011,2013 ve 2014 bu fuarlarda Pardus \
    standı kurulmuştur.2014 yılında ICT SummitT Now Bilişim Zirvesi'nde yer alınmıştır. \
    BİLİŞİM’2014 TBD 31. Ulusal Bilişim Kurultayı ve CITEX’2014 Ankara Bilişim Fuarı’na \
    Gümüş sponsorluk ile katkıda bulunulmuş ve Pardus standı kurulmuştur.",
    "question":"Pardus’un Google Summer of Code'a katıldığı yıllar nelerdir?"
    }
    
get_answer(question["question"],question["context"])
```
> 2008 ve 2009

### Example 2
```python
question2={
    "context":"II. Bayezid ve I. Selim devrinde yaşadı ve iki defa hekimbaşılık yaptı. \
    Böbrek ve idrar kesesindeki taş oluşumunun nedenlerini ve tedavisini incelediği \
    eseriyle tanınır. Adı kaynaklarda Ahmed ve Mahmud olarak da geçer. Ahi Çelebi \
    olarak ün yapmıştır. Babası Tabib Mevlana Kemal ile birlikte 1463’te İstanbul’a yerleşti. \
    Mevlana Kemal, devrin ünlü hekimlerindendir. Tebriz ya da Şirvan asıllı olduğu çeşitli \
    kaynaklarda belirtilir. Ahi Mehmet Çelebi, hekimliği daha çok babasından öğrendi. Onun \
    ölümünden sonra devrin önemli hekimleri Kutbüddin ile Altunîzâde’den ders alıp kısa zamanda \
    mesleğini ilerletti. Hekimlik becerisinin yanı sıra kuramsal bilgisiyle de kendisini \
    kabul ettirerek önce Fâtih Darüşşifasına hekim, sonra da başhekim oldu. II. Bayezid’in \
    güvenini kazanarak mutfak eminliğine, ardından da Hekimbaşılığa getirildi. Dört buçuk \
    yıl bu görevde kalan Ahî Çelebi, II. Bayezid’in ölümü üzerine geleneğe uyularak azledildi. \
    Bir müddet sonra Yavuz onu tekrar Hekimbaşılığa getirdi ve Mısır seferine beraberinde \
    götürdü. I. Selim'in ölümünden sonra Hekimbaşılık tan tekrar azledildi. Kaynakların \
    belirttiğine göre, yaşı doksanı geçmiş olduğu halde, hacdan dönerken Kahire’de \
    ölmüş ve İmam Şafi'nin kabri civarına defnedilmiştir.",
    "question":"Ahi Mehmet Çelebi hangi eseri ile tanınır?"
    }
    
get_answer(question2["question"],question2["context"])
```
> Böbrek ve idrar kesesindeki taş oluşumunun nedenlerini ve tedavisini incelediği eseriyle

Created by Özcan Gündeş ✌️
---

Twitter: <a href="https://twitter.com/ozcangundes" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/twitter.svg" alt="ozcangundes" height="30" width="30" /></a>
Linkedin: <a href="https://www.linkedin.com/in/%C3%B6zcan-g%C3%BCnde%C5%9F-7693055b/" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/linkedin.svg" alt="13198517" height="30" width="30" /></a>
Medium: <a href="https://medium.com/@ozcangundes" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/medium.svg" alt="@ozcangundes" height="30" width="30" /></a>
Github: <a href="https://github.com/ozcangundes" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg" alt="@ozcangundes" height="30" width="30" /></a>

