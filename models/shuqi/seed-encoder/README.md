# Less is More: Pre-train a Strong Text Encoder for Dense Retrieval Using a Weak Decoder

Please check the [official repository](https://github.com/microsoft/SEED-Encoder) for more details and updates.


# Fine-tuning on Marco passage/doc ranking tasks and NQ tasks

|   MSMARCO Dev Passage Retrieval    | MRR@10  | Recall@1k |
|------------------------------|---------------|--------------------- |
| BM25 warmup checkpoint     |     0.329     |      0.953     |
| ANCE Passage  checkpoint  |     0.334   |   0.961       |

|   MSMARCO Document Retrieval    | MRR@10 (Dev)  |  MRR@10 (Eval) |
|---------------- | -------------- | -------------- |
|  ANCE Document (FirstP)  checkpoint   |     0.394       |    0.362     | 


| NQ Task      | Top-1  |  Top-5    | Top-20  |  Top-100 |  MRR@20    | P@20  |
|---------------- | -------------- | -------------- |-------------- | -------------- | -------------- |-------------- |
| DPR checkpoint    |     46.1       |        68.8     |    80.4     |   87.1      |   56.2    |    20.1   |
| ANCE NQ checkpoint    |   52.5        |       73.1      |      83.1   |   88.7   |       61.5   |    22.5 


# Citation

If you find SEED-Encoder useful for your work, please cite the following paper:

 ```
  @article{lu2021less,
    title={Less is More: Pre-training a Strong Siamese Encoder Using a Weak Decoder},
    author={Lu, Shuqi and Xiong, Chenyan and He, Di and Ke, Guolin and Malik, Waleed and Dou, Zhicheng and Bennett, Paul and Liu, Tieyan and Overwijk, Arnold},
    journal={arXiv preprint arXiv:2102.09206},
    year={2021}
  }
 ```


