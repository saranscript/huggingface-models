---
language:
- de
tags:
- tinybert
- fill-mask
datasets:
- wiki
---


Here is represented tinybert model for German language (de). The model was created by distilling of bert base cased model(https://huggingface.co/dbmdz/bert-base-german-cased) in the way described in https://arxiv.org/abs/1909.10351 (TinyBERT: Distilling BERT for Natural Language Understanding)

Dataset:
German Wikipedia Text Corpus - https://github.com/t-systems-on-site-services-gmbh/german-wikipedia-text-corpus

Versions:
  torch==1.4.0
  transformers==4.8.1

How to load model for LM(fill-mask) task: 

  tokenizer = transformers.BertTokenizer.from_pretrained(model_dir + '/vocab.txt', do_lower_case=False)
  config = transformers.BertConfig.from_json_file(model_dir+'config.json')
  model = transformers.BertModel(config=config)
  model.pooler = nn.Sequential(nn.Linear(in_features=model.config.hidden_size, out_features=model.config.hidden_size, bias=True),
                               nn.LayerNorm((model.config.hidden_size,), eps=1e-12, elementwise_affine=True),
                               nn.Linear(in_features=model.config.hidden_size, out_features=len(tokenizer), bias=True))

  model.resize_token_embeddings(len(tokenizer))
    
  checkpoint = torch.load(model_dir+'/pytorch_model.bin', map_location=torch.device('cuda'))
  model.load_state_dict(checkpoint)


In case of NER or Classification task we have to load model for LM task and change pooler: 

  model.pooler = nn.Sequential(nn.Dropout(p=config.hidden_dropout_prob, inplace=False), 
                               nn.Linear(in_features=config.hidden_size, out_features=n_classes, bias=True))
                               
