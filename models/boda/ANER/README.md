---
language:
  - ar

thumbnail: "url to a thumbnail used in social sharing"
tags:
  - ner
  - token-classification
  - Arabic-NER


metrics:
  - accuracy
  - f1
  - precision
  - recall

widget:
  - text: "النجم محمد صلاح لاعب المنتخب المصري يعيش في مصر بالتحديد من نجريج, الشرقية"
    example_title: "Mohamed Salah"
  - text: "انا ساكن في حدايق الزتون و بدرس في جامعه عين شمس"
    example_title: "Egyptian Dialect"
  - text: "يقع نهر الأمازون في قارة أمريكا الجنوبية"
    example_title: "Standard Arabic"

datasets:
 - Fine-grained Arabic Named Entity Corpora

---
# Arabic Named Entity Recognition
This project is made to enrich the Arabic Named Entity Recognition(ANER). Arabic is a tough language to deal with and has alot of difficulties.
We managed to made a model based on Arabert to support 50 entities.

## Paper
Here's the paper that contains all the details for our model, our approach, and the training results 

- [ANER Paper](https://drive.google.com/file/d/1cNnKf-jS-3sjBXF2b0rkh517z9EzFFT4/view?usp=sharing)


# Usage 
 The model is available in HuggingFace model page under the  name:  [boda/ANER](https://huggingface.co/boda/ANER). Checkpoints are available only in PyTorch at the time.

### Use in python:
```python
from transformers import AutoTokenizer, AutoModelForTokenClassification

tokenizer = AutoTokenizer.from_pretrained("boda/ANER")

model = AutoModelForTokenClassification.from_pretrained("boda/ANER")
```




# Dataset
- [Fine-grained Arabic Named Entity Corpora](https://fsalotaibi.kau.edu.sa/Pages-Arabic-NE-Corpora.aspx)


# Acknowledgments
Thanks for [Arabert](https://github.com/aub-mind/arabert) for providing the Arabic Bert model, which we used as a base model for our work.

We also would like to thank [Prof. Fahd Saleh S Alotaibi](https://fsalotaibi.kau.edu.sa/Pages-Arabic-NE-Corpora.aspx) at Faculty of Computing and Information Technology King Abdulaziz University, for providing the dataset which we used to train our model with.

# Contacts

**Abdelrahman Atef** 
  - [LinkedIn](linkedin.com/in/boda-sadalla)
  - [Github](https://github.com/BodaSadalla98)
  -  <boda998@yahoo.com>
