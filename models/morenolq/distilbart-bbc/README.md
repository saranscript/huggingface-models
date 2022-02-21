This model is a fine-tuned version of [sshleifer/distilbart-cnn-12-6](https://huggingface.co/sshleifer/distilbart-cnn-12-6) on the BBC News Summary dataset (https://www.kaggle.com/pariza/bbc-news-summary).

The model has been generated as part of the in-lab practice of **Deep NLP course** currently held at Politecnico di Torino.

Training parameters:
- `num_train_epochs=2`
- `fp16=True`
- `per_device_train_batch_size=1`
- `warmup_steps=10`
- `weight_decay=0.01`
- `max_seq_length=100`