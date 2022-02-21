------------
## Arabic and English News Summarization NLP Model

### About

This model is for summarizing news stories in short highlights for both Arabic and English tasks.

نموذج معرفي متخصص في تلخيص الأخبار العربية و الإنجليزية الى مجموعة من أهم النقاط

### Fine-Tuning

The model was finetuned using the [Arabic T5 Model](https://huggingface.co/bakrianoo/t5-arabic-large) which developed by [Abu Bakr Soliman](http://github.com/bakrianoo).

The primary summarization model also developed by the same developer.

### How to Use

- You can use this [Colab Notebook](https://colab.research.google.com/drive/1DWND1CAfCXD4OxrfmLBEaKeXhjGmYkod?usp=sharing) to test the model

1. Install [PyTorch](https://pytorch.org/)

2. Install the following Python packages

`$ pip3 install transformers==4.7.0 nltk==3.5 protobuf==3.15.3 sentencepiece==0.1.96`

3. Run this code

```python

from transformers import AutoTokenizer, AutoModelWithLMHead
import torch
import nltk
nltk.download('punkt')
from nltk.tokenize import sent_tokenize

device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
m_name = "marefa-nlp/summarization-arabic-english-news"

tokenizer = AutoTokenizer.from_pretrained(m_name)
model = AutoModelWithLMHead.from_pretrained(m_name).to(device)

def get_summary(text, tokenizer, model, device="cpu", num_beams=2):
    if len(text.strip()) < 50:
        return ["Please provide more longer text"]
    
    text = "summarize: <paragraph> " + " <paragraph> ".join([ s.strip() for s in sent_tokenize(text) if s.strip() != ""]) + " </s>"
    text = text.strip().replace("\n","")
    
    tokenized_text = tokenizer.encode(text, return_tensors="pt").to(device)
    
    summary_ids = model.generate(
            tokenized_text,
            max_length=512,
            num_beams=num_beams,
            repetition_penalty=1.5, 
            length_penalty=1.0, 
            early_stopping=True
    )
    
    output = tokenizer.decode(summary_ids[0], skip_special_tokens=True)
    return [ s.strip() for s in output.split("<hl>") if s.strip() != "" ]
    
## Prepare Samples

samples = [
    """
        قال المدافع الإيطالي ليوناردو بونوتشي إن منتخب بلاده ليس خائفا من مواجهة نظيره الانجليزي على أرضه في المباراة النهائية في بطولة يورو 2020 لكرة القدم، في حين وصف المدافع الانجليزي جون ستونز المباراة المرتقبة بأنها ستكون "أكثر تميزا".
        وسوف تقام المباراة في استاد ويمبلي، شمال غربي لندن، يوم الأحد.
        وتسعى إيطاليا لإحراز اللقب الأوروبي للمرة الثانية بعد فوزها به أول مرة عام 1968.
        ولم يفز الفريق الانجليزي بهذا اللقب القاري من قبل. والبطولة الرئيسية الوحيدة التي فازت بها انجلترا هي كأس العالم عام 1966 الذي أقيمت مباراته النهائية في استاد ويمبلي.
    """,
    
    """
        On a night fraught with tension, Italy clinched its first major title for 15 years with a penalty shootout win over England in the Euro 2020 final.
        Luke Shaw's goal inside the opening two minutes gave England a lead it looked like it would hold onto all night, before a goalmouth scramble midway through the second half allowed Leonardo Bonucci to poke home an equalizer for Italy.
        For the remainder of the match, it felt as though extra-time and penalties were inevitable, as neither side seemed willing or brave enough to commit enough men forward to really trouble the opposing defenders.
        England had suffered innumerable heartbreaks on penalties over the years and this time it was Italy's turn to inflict yet more pain on beleaguered English fans as Marcus Rashford, Jadon Sancho and Bukayo Saka all missed from the spot.
    """,
]

## Get summaries

print("Original Article:", samples[0])
print("\n===========\nSummary: \n")
hls = get_summary(samples[0], tokenizer, model, device)
for hl in hls:
    print("\t-", hl)
    
    
print("Original Article:", samples[1])
print("\n=========== \nSummary: \n")
hls = get_summary(samples[1], tokenizer, model, device)
for hl in hls:
    print("\t-", hl)
```

Results

```
Original Article: 

        قال المدافع الإيطالي ليوناردو بونوتشي إن منتخب بلاده ليس خائفا من مواجهة نظيره الانجليزي على أرضه في المباراة النهائية في بطولة يورو 2020 لكرة القدم، في حين وصف المدافع الانجليزي جون ستونز المباراة المرتقبة بأنها ستكون "أكثر تميزا".
        وسوف تقام المباراة في استاد ويمبلي، شمال غربي لندن، يوم الأحد.
        وتسعى إيطاليا لإحراز اللقب الأوروبي للمرة الثانية بعد فوزها به أول مرة عام 1968.
        ولم يفز الفريق الانجليزي بهذا اللقب القاري من قبل. والبطولة الرئيسية الوحيدة التي فازت بها انجلترا هي كأس العالم عام 1966 الذي أقيمت مباراته النهائية في استاد ويمبلي.
    

===========
Summary: 

	- وسوف تواجه إيطاليا إنجلترا في بطولة يورو 2020 لكرة القدم يوم الأحد.
	- ستقام المباراة في استاد ويمبلي، شمال غربي لندن، يوم الأحد.
	- ولم يفز الفريق الانجليزي بهذا اللقب القاري قبل.
	
```

```
Original Article: 

        On a night fraught with tension, Italy clinched its first major title for 15 years with a penalty shootout win over England in the Euro 2020 final.
        Luke Shaw's goal inside the opening two minutes gave England a lead it looked like it would hold onto all night, before a goalmouth scramble midway through the second half allowed Leonardo Bonucci to poke home an equalizer for Italy.
        For the remainder of the match it felt as though extra-time and penalties were inevitable, as neither side seemed willing or brave enough to commit enough men forward to really trouble the opposing defenders.
        England had suffered innumerable heartbreaks on penalties over the years and this time it was Italy's turn to inflict yet more pain on beleaguered English fans as Marcus Rashford, Jadon Sancho and Bukayo Saka all missed from the spot.
    

=========== 
Summary: 

	- Luke Shaw's goal gave England a lead it looked like it would hold onto all night.
	- Leonardo Bonucci scored the equalizer for Italy.
	- Marcus Rashford, Jadon Sancho and Bukayo Saka all missed.
```
