---
license: mit
widget:
- text: "Apoorv Saxena| family name"
  example_title: "Family name prediction"
- text: "Apoorv Saxena| country"
  example_title: "Country prediction"
- text: "World War 2| followed by"
  example_title: "followed by"
- text: "Q12345678| follows"
  example_title: "follows"
---
This is a t5-small model trained from scratch on WikiKG90Mv2 dataset. Please see https://github.com/apoorvumang/transformer-kgc/ for more details on the method.

This model was trained on the tail entity prediction task ie. given subject entity and relation, predict the object entity. Input should be provided in the form of "\<entity text\>| \<relation text\>".

We used the raw text title and descriptions to get entity and relation textual representations. These raw texts were obtained from ogb dataset itself (dataset/wikikg90m-v2/mapping/entity.csv and relation.csv). Entity representation was set to the title, and description was used to disambiguate if 2 entities had the same title. If still no disambiguation was possible, we used the wikidata ID (eg. Q123456).

We trained the model on WikiKG90Mv2 for approx 1.5 epochs on 4x1080Ti GPUs. The training time for 1 epoch was approx 5.5 days.

To evaluate the model, we sample 300 times from the decoder for each input (s,r) pair. We then remove predictions which do not map back to a valid entity, and then rank the predictions by their log probabilities. Filtering was performed subsequently.

You can try the following code in an ipython notebook to evaluate the pre-trained model. The full procedure of mapping entity to ids, filtering etc. is not included here for sake of simplicity but can be provided on request if needed. Please contact Apoorv (apoorvumang@gmail.com) for clarifications/details.
---------
```
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
tokenizer = AutoTokenizer.from_pretrained("apoorvumang/kgt5-wikikg90mv2")
model = AutoModelForSeq2SeqLM.from_pretrained("apoorvumang/kgt5-wikikg90mv2")
```
```
import torch

def getScores(ids, scores, pad_token_id):
    """get sequence scores from model.generate output"""
    scores = torch.stack(scores, dim=1)
    log_probs = torch.log_softmax(scores, dim=2)
    # remove start token
    ids = ids[:,1:]
    # gather needed probs
    x = ids.unsqueeze(-1).expand(log_probs.shape)
    needed_logits = torch.gather(log_probs, 2, x)
    final_logits = needed_logits[:, :, 0]
    padded_mask = (ids == pad_token_id)
    final_logits[padded_mask] = 0
    final_scores = final_logits.sum(dim=-1)
    return final_scores.cpu().detach().numpy()

def topkSample(input, model, tokenizer, 
                num_samples=5,
                num_beams=1,
                max_output_length=30):
    tokenized = tokenizer(input, return_tensors="pt")
    out = model.generate(**tokenized,
                        do_sample=True,
                        num_return_sequences = num_samples,
                        num_beams = num_beams,
                        eos_token_id = tokenizer.eos_token_id,
                        pad_token_id = tokenizer.pad_token_id,
                        output_scores = True,
                        return_dict_in_generate=True,
                        max_length=max_output_length,)
    out_tokens = out.sequences
    out_str = tokenizer.batch_decode(out_tokens, skip_special_tokens=True)
    out_scores = getScores(out_tokens, out.scores, tokenizer.pad_token_id)
    
    pair_list = [(x[0], x[1]) for x in zip(out_str, out_scores)]
    sorted_pair_list = sorted(pair_list, key=lambda x:x[1], reverse=True)
    return sorted_pair_list

def greedyPredict(input, model, tokenizer):
    input_ids = tokenizer([input], return_tensors="pt").input_ids
    out_tokens = model.generate(input_ids)
    out_str = tokenizer.batch_decode(out_tokens, skip_special_tokens=True)
    return out_str[0]
```

```
# an example from validation set that the model predicts correctly
# you can try your own examples here. what's your noble title?
input = "Sophie Valdemarsdottir| noble title"
out = topkSample(input, model, tokenizer, num_samples=5)
out
```

You can further load the list of entity aliases, then filter only those predictions which are valid entities then create a reverse mapping from alias -> integer id to get final predictions in required format.

However, loading these aliases in memory as a dictionary requires a lot of RAM + you need to download the aliases file (made available here)

The submitted validation/test results for were obtained by sampling 300 times for each input, then applying above procedure, followed by filtering known entities. The final MRR can vary slightly due to this sampling nature (we found that although beam search gives deterministic output, the results are inferior to sampling large number of times).

```
# download valid.txt. you can also try same url with test.txt. however test does not contain the correct tails
!wget https://storage.googleapis.com/kgt5-wikikg90mv2/valid.txt
```
```
fname = 'valid.txt'
valid_lines = []
f = open(fname)
for line in f:
    valid_lines.append(line.rstrip())
f.close()
print(valid_lines[0])
```
```
from tqdm.auto import tqdm
# try unfiltered hits@k. this is approximation since model can sample same seq multiple times
# you should run this on gpu if you want to evaluate on all points with 300 samples each
k = 1
count_at_k = 0
max_predictions = k
max_points = 1000
for line in tqdm(valid_lines[:max_points]):
    input, target = line.split('\t')
    model_output = topkSample(input, model, tokenizer, num_samples=max_predictions)
    prediction_strings = [x[0] for x in model_output]
    if target in prediction_strings:
        count_at_k += 1
print('Hits at {0} unfiltered: {1}'.format(k, count_at_k/max_points))
```