* Fine-tunning "KLUE/roberta-large" model For CER(Company Entity Recognition) With Custom Dataset
  * Custom Datasets are composed of news data

```python

label_list = ['O',"B-PER","I-PER","B-ORG","I-ORG","B-COM","I-COM","B-LOC","I-LOC","B-DAT","I-DAT","B-TIM","I-TIM","B-QNT","I-QNT"]

refer_list = ['0','1','2','3','4','5','6','7','8','9','10','11','12','13','14']


```
- EX: "B-PER" : 1 , "B-COM" : 5