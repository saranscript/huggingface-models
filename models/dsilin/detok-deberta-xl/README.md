---
language: english
widget:
- text: "They 're a young team . they have great players and amazing freshmen coming in , so think they 'll grow into themselves next year ,"
- text: "\" We 'll talk go by now ; \" says Shucksmith ;"
- text: "\" Warren Gatland is a professional person and it wasn 't a case of 's I 'll phone my mate Rob up to if he wants a coaching job ' , he would done a fair amount of homework about , \" Howley air said ."
---

This model can be used to more accurately detokenize the moses tokenizer (it does a better job with certain lossy quotes and things)


batched usage: 

```python

sentences = [
    "They 're a young team . they have great players and amazing freshmen coming in , so think they 'll grow into themselves next year ,",
    "\" We 'll talk go by now ; \" says Shucksmith ;",
    "He 'll enjoy it more now that this he be dead , if put 'll pardon the expression .",
    "I think you 'll be amazed at this way it finds ,",
    "Michigan voters ^ are so frightened of fallen in permanent economic collapse that they 'll grab onto anything .",
    "You 'll finding outs episode 4 .",
    "\" Warren Gatland is a professional person and it wasn 't a case of 's I 'll phone my mate Rob up to if he wants a coaching job ' , he would done a fair amount of homework about , \" Howley air said .",
    "You can look at the things I 'm saying about my record and about the events of campaign and history and you 'll find if now and and then I miss a words or I get something slightly off , I 'll correct it , acknowledge where it are wrong .",
    "Wonder if 'll alive to see .",
    "We 'll have to combine and a numbered of people ."
]

def sentences_to_input_tokens(sentences):
    all_tokens = []
    max_length = 0
    sents_tokens = []
    iids = tokenizer(sentences)
    for sent_tokens in iids['input_ids']:        
        sents_tokens.append(sent_tokens)
        
        if len(sent_tokens) > max_length:
            max_length = len(sent_tokens)
            
        attention_mask = [1] * len(sent_tokens)
        pos_ids = list(range(len(sent_tokens)))

        encoding = {
            "iids": sent_tokens,
            "am": attention_mask,
            "pos": pos_ids
        }
        
        all_tokens.append(encoding)
    
    input_ids = []
    attention_masks = []
    position_ids = []
    for i in range(len(all_tokens)):
        
        encoding = all_tokens[i]
        
        pad_len = max_length - len(encoding['iids'])
        attention_masks.append(encoding['am'] + [0] * pad_len)
        position_ids.append(encoding['pos'] + [0] * pad_len)
        input_ids.append(encoding['iids'] + [tokenizer.pad_token_id] * pad_len)        
    
    encoding = {
        "input_ids": torch.tensor(input_ids).to(device),
        "attention_mask": torch.tensor(attention_masks).to(device),
        "position_ids": torch.tensor(position_ids).to(device)
    }
        
    return encoding, sents_tokens

def run_token_predictor_sentences(sentences):
    encoding, at = sentences_to_input_tokens(sentences)
    predictions = model(**encoding)[0].cpu().tolist()
    outstrs = []

    for i in range(len(predictions)):
        outstr = ""
        for p in zip(tokenizer.convert_ids_to_tokens(at[i][1:-1]), predictions[i][1:-1]):
            if not "▁" in p[0]:
                outstr+=p[0]
            else:
                if p[1][0] > p[1][1]:
                    outstr+=p[0].replace("▁", " ")
                else:
                    outstr+=p[0].replace("▁", "")
        outstrs.append(outstr.strip())
    return outstrs
    
outs = run_token_predictor_sentences(sentences)
for p in zip(outs, sentences):
    print(p[1])
    print(p[0])
    print('\n------\n')
    
```