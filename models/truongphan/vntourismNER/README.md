# Vietnam Tourism Named Entity Recognition (English version)
We fine-tuned BERT to train Vietnam tourism dataset for a question answering system. The model was called NER2QUES because it detected tourism NER in a sentence. From that, the system generated questions corresponding to NER types.
# How to use
## You can use in Transformers
  
    from transformers import AutoTokenizer, AutoModelForTokenClassification
  
    tokenizer = AutoTokenizer.from_pretrained("truongphan/vntourismNER")

    model = AutoModelForTokenClassification.from_pretrained("truongphan/vntourismNER")
    
    custom_labels = [
    "O", "B-TA", "I-TA", "B-PRO", "I-PRO", "B-TEM", "I-TEM", "B-COM", "I-COM", "B-PAR", "I-PAR", "B-CIT", "I-CIT",
    "B-MOU", "I-MOU", "B-HAM", "I-HAM", "B-AWA", "I-AWA", "B-VIS", "I-VIS", "B-FES", "I-FES", "B-ISL", "I-ISL",
    "B-TOW", "I-TOW", "B-VIL", "I-VIL", "B-CHU", "I-CHU", "B-PAG", "I-PAG", "B-BEA", "I-BEA", "B-WAR", "I-WAR",
    "B-WAT", "I-WAT", "B-SA", "I-SA", "B-SER", "I-SER", "B-STR", "I-STR", "B-NUN", "I-NUN", "B-PAL", "I-PAL",
    "B-VOL", "I-VOL", "B-HIL", "I-HIL", "B-MAR", "I-MAR", "B-VAL", "I-VAL", "B-PROD", "I-PROD", "B-DIS", "I-DIS",
    "B-FOO", "I-FOO", "B-DISH", "I-DISH", "B-DRI", "I-DRI"
    ]
    line = "King Garden is located in Thanh Thuy, Phu Tho province"

    nlp = pipeline('ner', model=model, tokenizer=tokenizer)

    ner_rs = nlp(line)
    for k in ner_rs:
      print(custom_labels[int(str(k['entity']).replace('LABEL_',''))], '-', k['word'])
    

# Authors

1. Phuc Do, University of Information Technology, Ho Chi Minh national university, Vietnam

  Email: <phucdo@uit.edu.vn>
  
  Link *[Google scholar](https://scholar.google.com/citations?user=qv1WUzcAAAAJ&hl=vi)*
  
2. Truong H. V. Phan, Van Lang university, Ho Chi Minh city, Vietnam

  Email: <truong.phv@vlu.edu.vn>
  
  Link *[Google scholar](https://scholar.google.com/citations?hl=vi&user=cDexuHEAAAAJ)*

# Citation
If you use the model in your work, please cite our paper

Phan, T.H.V., Do, P. NER2QUES: combining named entity recognition and sequence to sequence to automatically generating Vietnamese questions. Neural Comput & Applic (2021). https://doi.org/10.1007/s00521-021-06477-7