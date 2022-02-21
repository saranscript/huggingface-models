# Twitter-roBERTa-base_SemEval18_Emodetection

This is a Twitter-roBERTa-base model trained on ~7000 tweets in English annotated for 11 emotion categories in [SemEval-2018 Task 1: Affect in Tweets: SubTask 5: Emotion Classification](https://competitions.codalab.org/competitions/17751). 

Run the classifier on the test set of the competition:

```python
from datasets import load_dataset
from transformers import AutoTokenizer, AutoModel
from torch.utils.data import DataLoader
import torch
import pandas as pd

# choose GPU when available
device = 'cuda' if torch.cuda.is_available() else 'cpu'

tokenizer = AutoTokenizer.from_pretrained("cardiffnlp/twitter-roberta-base",model_max_length=512)

# build custom model with classification layer on top and a dropout layer before
class RobertaClass(torch.nn.Module):
    
    def __init__(self):
        super(RobertaClass, self).__init__()
        self.l1 = AutoModel.from_pretrained("cardiffnlp/twitter-roberta-base",return_dict=False)
        self.l2 = torch.nn.Dropout(0.3)
        self.l3 = torch.nn.Linear(768, 11)
        
    def forward(self, input_ids, attention_mask):
        _, output_1= self.l1(input_ids=input_ids, attention_mask=attention_mask)
        output_2 = self.l2(output_1)
        output = self.l3(output_2)
        
        return output

model_name="twitter-roberta-base_semeval18_emodetection/pytorch_model.bin"

model=RobertaClass()

model.load_state_dict(torch.load(model_name,map_location=torch.device(device)))

model.eval()

# run on more than 1 GPU
model = torch.nn.DataParallel(model)

model.to(device)

twnames=['anger','anticipation','disgust','fear','joy','love','optimism','pessimism','sadness','surprise','trust']

# load from hugging face dataset hub
testset_raw = load_dataset('sem_eval_2018_task_1','subtask5.english',split='test')

# remove old columns
testset=testset_raw.remove_columns(twnames+["ID"])

# tokenize
testset_tokenized = testset.map(lambda e: tokenizer(e['Tweet'], truncation=True, padding='max_length'), batched=True)

testset_tokenized=testset_tokenized.remove_columns("Tweet")

testset_tokenized.set_format(type='torch', columns=['input_ids', 'attention_mask'])


outfile="predicted_2018-E-c-En-test-gold.txt"

MAX_LEN = 512
VALID_BATCH_SIZE = 8
# set batch size according to available RAM
# VALID_BATCH_SIZE = 1000

# set num_workers for parallel processing
inference_params = {'batch_size': VALID_BATCH_SIZE,
                'shuffle': False,
                # 'num_workers': 1
                }

inference_loader = DataLoader(testset_tokenized, **inference_params)


open(outfile,"w").close()
with torch.no_grad():
    # change lines for progress manager
    # for _, data in tqdm(enumerate(inference_loader, 0),total=len(inference_loader)):
    for _, data in enumerate(inference_loader, 0):
        outputs = model(input_ids=data['input_ids'],attention_mask=data['attention_mask'])
        fin_outputs=torch.sigmoid(outputs).cpu().detach().numpy().tolist()
        pd.DataFrame(fin_outputs).to_csv(outfile,index=False,header=False,sep="\t",mode='a')
        
        
# # dataset from file (one text per line)
# from datasets import Dataset

# with open(linesoftextfile,"rb") as textfile:
#     textdict={"text":[x.decode().rstrip("\n") for x in textfile.readlines()]}
    
# inference_dataset=Dataset.from_dict(textdict)
# del(textdict)
```