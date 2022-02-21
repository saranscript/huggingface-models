# BERT MCN-Model using SMM4H 2017 (subtask 3) data

The model was trained using [clagator/biobert_v1.1_pubmed_nli_sts](https://huggingface.co/clagator/biobert_v1.1_pubmed_nli_sts) as a base and the smm4h dataset from 2017 from subtask 3. 

## Dataset

See [here](https://github.com/olastor/medical-concept-normalization/tree/main/data/smm4h) for the scripts and datasets.

**Attribution**

Sarker, Abeed (2018), “Data and systems for medication-related text classification and concept normalization from Twitter: Insights from the Social Media Mining for Health (SMM4H)-2017 shared task”, Mendeley Data, V2, doi: 10.17632/rxwfb3tysd.2

### Test Results

- Acc: 89.44 
- Acc@2: 91.84 
- Acc@3: 93.20
- Acc@5: 94.32
- Acc@10: 95.04

Acc@N denotes the accuracy taking the top N predictions of the model into account, not just the first one. 