This Model is a fine-tuned version of T-systems [summarization model v1](https://huggingface.co/deutsche-telekom/mt5-small-sum-de-en-v1). 

We used 1000 examples of headline-content pairs from BR24 articles for the fine-tuning process.

Despite the small amount of training data, the tonality of the summarizations has changed significantly. Many of the resulting summaries do sound like a headline.

## Training

We used the following parameters for training this model:

+ base model: deutsche-telekom/mt5-small-sum-de-en-v1
+ source_prefix: "summarize: "
+ batch size: 4
+ max_source_length: 400
+ max_target_length: 35
+ weight_decay: 0.01
+ number of train epochs: 1
+ learning rate: 5e-5

## License

Since the base model is trained on the MLSUM dataset, this model may not be used for commercial use.

## Stats

| Model                                   | Rouge1    | Rouge2   | RougeL    | RougeLSum |
|-----------------------------------------|-----------|----------|-----------|-----------|
| headlines_test_small_example            | 13.573500 | 3.694700 | 12.560600 | 12.60000  |
| deutsche-telekom/mt5-small-sum-de-en-v1 | 10.6488   | 2.9313   | 10.0527   | 10.0523   |

