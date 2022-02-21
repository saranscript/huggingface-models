# BERT2BERT temporal tagger 

Seq2seq model for temporal tagging of plain text using BERT language model. The model is introduced in the paper BERT got a Date: Introducing Transformers to Temporal Tagging and release in this [repository](https://github.com/satya77/Transformer_Temporal_Tagger).
RoBERTa version of the same model is also available [here](https://huggingface.co/satyaalmasian/temporal_tagger_roberta2roberta) and has better performance.

# Model description
BERT is a transformers model pretrained on a large corpus of English data in a self-supervised fashion. We use BERT in an encoder-decoder architecture for text generation, where the input is raw text and the output is the temporally annotated text. The model is pre-trained on a weakly annotated dataset from a rule-based system (HeidelTime) and fine-tuned on the temporal benchmark datasets (Wikiwars, Tweets, Tempeval-3). 

# Intended uses & limitations
This model is best used accompanied with code from the [repository](https://github.com/satya77/Transformer_Temporal_Tagger). Especially for inference, the direct output might be noisy and hard to decipher, in the repository we provide cleaning functions for the output and insert the temporal tags from the generated text in the input text. If you have temporally annotated data you can fine-tune this model. 

# How to use
you can load the model as follows:
```
tokenizer = AutoTokenizer.from_pretrained("satyaalmasian/temporal_tagger_BERT_tokenclassifier")
model = EncoderDecoderModel.from_pretrained("satyaalmasian/temporal_tagger_BERT_tokenclassifier")

```
for inference use: 
```
model_inputs = tokenizer(input_text, truncation=True, return_tensors="pt")
out = model.generate(**model_inputs)
decoded_preds = tokenizer.batch_decode(out, skip_special_tokens=True)

```
for an example with post-processing, refer to the [repository](https://github.com/satya77/Transformer_Temporal_Tagger).
to further fine-tune, use the `Seq2SeqTrainer` from hugginface. An example of a similar fine-tuning can be found [here](https://github.com/satya77/Transformer_Temporal_Tagger/blob/master/run_seq2seq_bert_roberta.py).
```
trainer = Seq2SeqTrainer(
        model=model2model,
        tokenizer=tokenizer,
        args=training_args,
        compute_metrics=metrics.compute_metrics,
        train_dataset=train_data,
        eval_dataset=val_data,
    )

    train_result=trainer.train()
```
where the `training_args` is an instance of `Seq2SeqTrainingArguments`. 
#Training data
We use four data sources: 
For Pretraining :1 million weakly annotated samples from heideltime. The samples are from news articles between the 1st January 2019 and the 30th July. 
Fine-tunning: [Tempeval-3](https://www.cs.york.ac.uk/semeval-2013/task1/index.php%3Fid=data.html), Wikiwars, Tweets datasets. For the correct data versions please refer to our [repository](https://github.com/satya77/Transformer_Temporal_Tagger). 

#Training procedure
 The model is pre-trained on the weakly labeled data for $3$ epochs on the train set, from publicly available checkpoints on huggingface (`bert-base-uncased`), with a batch size of 12. We use a learning rate of 5e-05 with an Adam optimizer and linear weight decay.
Additionally, we use 2000 warmup steps. 
We fine-tune the 3 benchmark data for 8 epochs with 5 different random seeds, this version of the model is the only seed=4.
The batch size and the learning rate is the same as the pre-training setup, but the warm-up steps are reduced to 100.
For training, we use 2 NVIDIA A100 GPUs with 40GB of memory. 
For inference in seq2seq models, we use Greedy decoding, since beam search had sub-optimal results.

 


