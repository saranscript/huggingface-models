# Korean bert base model for DST

- This is ConversationBert for dsksd/bert-ko-small-minimal(base-module) + 5 datasets
- Use dsksd/bert-ko-small-minimal tokenizer
- 5 datasets
  - tweeter_dialogue : xlsx
  - speech : trn
  - office_dialogue : json
  - KETI_dialogue : txt
  - WOS_dataset : json
  
```python
tokenizer = AutoTokenizer.from_pretrained("BonjinKim/dst_kor_bert")
model = AutoModel.from_pretrained("BonjinKim/dst_kor_bert")
```