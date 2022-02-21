## Roberta-Base

This repo trains [roberta-base](https://huggingface.co/roberta-base) from scratch on the [Norwegian training subset of Oscar](https://oscar-corpus.com/) containing roughly 4.7 GB of data according to [this](https://github.com/huggingface/transformers/tree/master/examples/flax/language-modeling) example.

Training is done on a TPUv3-8 in Flax. More statistics on the training run can be found under [tf.hub](https://tensorboard.dev/experiment/GdYmdak2TWeVz0DDRYOrrg).
