# albertZero

albertZero is a PyTorch model with a prediction head fine-tuned for SQuAD 2.0.  

Based on Hugging Face's albert-base-v2, albertZero employs a novel method to speed up fine-tuning.  It re-initializes weights of final linear layer in the shared albert transformer block, resulting in a 2% point improvement during the early epochs of fine-tuning.



## Usage

albertZero can be loaded like this:

```python
tokenizer = AutoTokenizer.from_pretrained('MarshallHo/albertZero-squad2-base-v2')
model = AutoModel.from_pretrained('MarshallHo/albertZero-squad2-base-v2')

```

or 

```python
from transformers import AlbertModel, AlbertTokenizer, AlbertForQuestionAnswering, AlbertPreTrainedModel

mytokenizer = AlbertTokenizer.from_pretrained('albert-base-v2')
model = AlbertForQuestionAnsweringAVPool.from_pretrained('albert-base-v2')
model.load_state_dict(torch.load('albertZero-squad2-base-v2.bin'))
```


## References

The goal of [ALBERT](https://arxiv.org/abs/1909.11942) is to reduce the memory requirement of the groundbreaking
language model [BERT](https://arxiv.org/abs/1810.04805), while providing a similar level of performance. ALBERT mainly uses 2 methods to reduce the number of parameters – parameter sharing and factorized embedding.  

The field of NLP has undergone major improvements in recent years. The
replacement of recurrent architectures by attention-based models has allowed NLP tasks such as
question-answering to approach human level performance. In order to push the limits further, the
[SQuAD2.0](https://arxiv.org/abs/1806.03822) dataset was created in 2018 with 50,000 additional unanswerable questions, addressing a major weakness of the original version of the dataset.

At the time of writing, near the top of the [SQuAD2.0 leaderboard](https://rajpurkar.github.io/SQuAD-explorer/) is Shanghai Jiao Tong University’s [Retro-Reader](http://arxiv.org/abs/2001.09694).
We have re-implemented their non-ensemble ALBERT model with the SQUAD2.0 prediction head.



## Acknowledgments

Thanks to the generosity of the team at Hugging Face and all the groups referenced above !