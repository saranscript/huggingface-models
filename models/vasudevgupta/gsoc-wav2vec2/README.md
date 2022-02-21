Wav2Vec2 Model (initialized from [`facebook/wav2vec2-base`](https://huggingface.co/facebook/wav2vec2-base)) with **no** LM head.

Model weights are converted into TensorFlow using following script:

```shell
python3 convert_torch_to_tf.py --hf_model_id "facebook/wav2vec2-base"
```

**TF SavedModel** is obtained by running following commands:

```shell
git clone https://huggingface.co/vasudevgupta/gsoc-wav2vec2

python3 export2hub.py \
--hf_model_id facebook/wav2vec2-base \
--saved_model_dir gsoc-wav2vec2/saved-model \
--seqlen 246000

cd gsoc-wav2vec2 && tar -czf saved-model.tar.gz saved-model
```

Project Link: https://github.com/vasudevgupta7/gsoc-wav2vec2
