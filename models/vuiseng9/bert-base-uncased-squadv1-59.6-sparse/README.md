* A set of unstructured sparse bert-base-uncased models fine-tuned for SQuADv1.
* Tensorflow models are created using ```TFAutoModelForQuestionAnswering.from_pretrained(..., from_pt=True)``` and ```model.save_pretrained(tf_pth)```.
* Observed issue - loss in model translation, discrepancy observed in evaluation between pytorch and tensorflow models.
* Table below is evaluated in HF's transformers v4.9.2. Sparsity is normalized to dense layers in attention heads and FFNN.
* Evaluation cli:
    ```bash
    python run_qa.py \
        --model_name_or_path <model identifier> \
        --dataset_name squad \
        --do_eval \
        --per_device_eval_batch_size 384 \
        --max_seq_length 68 \
        --doc_stride 26 \
        --output_dir /tmp/eval-squad
    ```


|    | HF Model Hub Identifier                                                                                                 |   sparsity |   em (pytorch) |   em (tf) |   f1 (pytorch) |   f1 (tf) |
|---:|:------------------------------------------------------------------------------------------------------------------------|-----------:|---------------:|----------:|---------------:|----------:|
|  0 | [vuiseng9/bert-base-uncased-squadv1-85.4-sparse](https://huggingface.co/vuiseng9/bert-base-uncased-squadv1-85.4-sparse) |       85.4 |        69.9338 |   14.2573 |        77.6861 |   23.4917 |
|  1 | [vuiseng9/bert-base-uncased-squadv1-72.9-sparse](https://huggingface.co/vuiseng9/bert-base-uncased-squadv1-72.9-sparse) |       72.9 |        74.6358 |   31.0596 |        82.2555 |   39.8446 |
|  2 | [vuiseng9/bert-base-uncased-squadv1-65.1-sparse](https://huggingface.co/vuiseng9/bert-base-uncased-squadv1-65.1-sparse) |       65.1 |        76.1306 |   43.0274 |        83.4117 |   51.4300 |
|  3 | [vuiseng9/bert-base-uncased-squadv1-59.6-sparse](https://huggingface.co/vuiseng9/bert-base-uncased-squadv1-59.6-sparse) |       59.6 |        76.8590 |   50.4920 |        84.1267 |   59.0881 |
|  4 | [vuiseng9/bert-base-uncased-squadv1-52.0-sparse](https://huggingface.co/vuiseng9/bert-base-uncased-squadv1-52.0-sparse) |       52.0 |        78.0038 |   54.2857 |        85.2000 |   62.2914 |