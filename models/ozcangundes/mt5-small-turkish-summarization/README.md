---
language: tr
datasets:
- MLSUM
pipeline_tag: summarization
license: mit
---

# mT5-small based Turkish Summarization System

[Google's Multilingual T5-small](https://github.com/google-research/multilingual-t5) is fine-tuned on [MLSUM Turkish news dataset](https://github.com/recitalAI/MLSUM) for **Summarization** downstream task by using Pytorch Lightning.⚡  

mT5 small model has 300 million parameters and model size is about 1.2GB. Therefore, it takes significant amount of time to fine tune it. The model is trained with 10 epochs, 8 batch size and 10e-4 learning rate. It took almost 4 hours. The max news length is kept as 784 and max summary length is determined as 64. 


**Important Note**: mT5 was only pre-trained on [mC4](https://www.tensorflow.org/datasets/catalog/c4#c4multilingual)
excluding any supervised training. Therefore, the mT5 model has to be fine-tuned before it is useable on a downstream task.

## Dataset

MLSUM dataset has more than 250K Turkish news with their related summaries. Since the mT5 model size and vocabulary is so large, 20K data is used for training and 4K data is used for validation. For more information about the dataset, please read this [great paper](https://arxiv.org/abs/2004.14900).
## Usage 🚀

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

tokenizer = AutoTokenizer.from_pretrained("ozcangundes/mt5-small-turkish-summarization")

model = AutoModelForSeq2SeqLM.from_pretrained("ozcangundes/mt5-small-turkish-summarization")

def generate_summary(main_news):
  source_encoding=tokenizer(
    main_news,
    max_length=784,
    padding="max_length",
    truncation=True,
    return_attention_mask=True,
    add_special_tokens=True,
    return_tensors="pt")
  
  generated_ids=model.generate(
      input_ids=source_encoding["input_ids"],
      attention_mask=source_encoding["attention_mask"],
      num_beams=2,
      max_length=120,
      repetition_penalty=2.5,
      length_penalty=2.0,
      early_stopping=True,
      use_cache=True
  )

  preds=[tokenizer.decode(gen_id, skip_special_tokens=True, clean_up_tokenization_spaces=True) 
         for gen_id in generated_ids]

  return "".join(preds)
```

### Example 1
```python
main_news= "Final etabının üçüncü karşılaşması 29 Nisan Pazartesi günü saat 18.00 ’ de Burhan Felek
           Voleybol Salonu ’ nda oynanacak . Sezonu FIVB Kulüpler Dünya Şampiyonluğu ile açan ve CEV 
           Avrupa Şampiyonlar Ligi'ni üçüncü olarak tamamlayan VakıfBank Kadın Voleybol Takımı , 
           Vestel Venus Sultanlar Ligi final serisi ikinci maçında Eczacıbaşı VitrA'yı VakıfBank 
           Spor Sarayı'nda 16-25 , 25-10 , 25-18 ve 25-17'lik setlerle 3-1 mağlup ederek seride durumu
           1-1 ' e getirdi . İlk setini 25-16 kaybettiği karşılaşmanın ikinci setinde etkili servisler
           kullanan sarı-siyahlılar , teknik molasına 12-5 önde girdiği seti 25-10 almayı başardı . 
           Etkili servis performansını üçüncü sette de sürdüren VakıfBank , teknik molasına 12-5 önde 
           girdiği seti 25-18 alarak , karşılaşmada 2-1 öne geçti . Dördüncü sette rakibinin geri dönüşüne 
           izin vermeyen VakıfBank , seti 25-17 , maçı da 3-1 kazanarak seride durumu eşitledi."
    
generate_summary(main_news)

#original summary -> "Vestel Venus Sultanlar Ligi final etabı ikinci karşılaşmasında VakıfBank 
                  kendi sahasında Eczacıbaşı VitrA'yı 3-1 mağlup etti ve seride durumu 1-1 ' e getirdi ."

#output -> "CEV Avrupa Şampiyonlar Ligi'ni üçüncü olarak tamamlayan VakıfBank Kadın Voleybol Takımı, 
            Vestel Venus Sultanlar Ligi final serisi ikinci maçında Eczacıbaşı VitrA'yı 3-1 mağlup 
            ederek seride durumu 1-1'e getirdi."
```

### Example 2
```python
main_news="2023'te yerli tank motoru : Bir taraftan da tankın motorunu yerlileştirmeye çalıştıklarını 
          ifade eden Öztürk , şu değerlendirmelerde bulundu : `` Bin 500 beygirlik , şanzımanıyla beraber 
          motoru yerlileştirmeye çalışıyoruz . Bu da bir aksilik çıkmazsa ilk tankımızın üzerine 
          2023'te koyacağız . Bundan sonra hiçbir ülkeye bağımlılığımız kalmadan bu araçları üretmeye
           devam edeceğiz . Sorumluluğumuzun ağır olduğunu biliyoruz . Ülkemize hizmet etmeye çalışıyoruz .
           Bunu daha da ileriye götürmek için elimizden gelen çabayı sarf ediyoruz . Ama bu tek başınıza
           yapılan bir operasyon değil . Türkiye'deki yerli firmalarla beraber ortaklaşa bu işi yürütmeye çalışıyoruz."
    
generate_summary(main_news)

#output -> "TÜRKİYE'de bir taraftan da tankın motorunu yerlileştirmeye çalıştıklarını belirten Öztürk, 
            `` Bin 500 beygirlik, şanzımanıyla beraber motoru yerlileştirmeye çalışıyoruz. Bu da bir 
            aksilik çıkmazsa ilk tankımızın üzerine 2023'te koyacağız.'' dedi."
```

Created by Özcan Gündeş ✌️
---

Twitter: <a href="https://twitter.com/ozcangundes" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/twitter.svg" alt="ozcangundes" height="30" width="30" /></a>
Linkedin: <a href="https://www.linkedin.com/in/%C3%B6zcan-g%C3%BCnde%C5%9F-7693055b/" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/linkedin.svg" alt="13198517" height="30" width="30" /></a>
Medium: <a href="https://medium.com/@ozcangundes" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/medium.svg" alt="@ozcangundes" height="30" width="30" /></a>
Github: <a href="https://github.com/ozcangundes" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg" alt="@ozcangundes" height="30" width="30" /></a>
