This model trains [T5-V1_1-base](https://huggingface.co/google/t5-v1_1-base) on the Norwegian dataset of [Oscar](https://huggingface.co/datasets/oscar). Note that the original configuration is slightly change (dropout is set to 0).

The official [run_t5_mlm_flax.py](https://github.com/huggingface/transformers/blob/master/examples/flax/language-modeling/run_t5_mlm_flax.py) is copied into the repository and is run using the hyperparameters as defined in *run_t5.sh*.

Training loss can be seen directly on the model card. The full training runs in finished in ca. 4 hours and 30 minutes.
