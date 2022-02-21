---
language: ar
tags:
- speech
- audio
license: cc-by-nc-4.0
---

# Arabic Hubert-Large

This model was pre-trained on 2,000 hours of 16kHz sampled Arabic speech audio. When using the model make sure that your speech input is also sampled at 16Khz. [Paper](https://arxiv.org/abs/2106.07447).

Training of this mode was performed using [fairseq](https://github.com/pytorch/fairseq). Tensorboard logs of the training can be found [here](https://tensorboard.dev/experiment/AWc8Zj8kQ8KQgL0ytRsMFA/#scalars)

**Note**: This model does not have a tokenizer as it was pretrained on audio alone. In order to use this model **speech recognition**, a tokenizer should be created and the model should be fine-tuned on labeled text data.

# Usage

See [this blog](https://huggingface.co/blog/fine-tune-wav2vec2-english) for more information on how to fine-tune the model. Note that the class `Wav2Vec2ForCTC` has to be replaced by `HubertForCTC`.

# License

This work is licensed under CC BY-NC-4.0.

# Acknowledgments

Model pre-training and data processing for in this work partially performed at [KUIS AI Center](ai.ku.edu.tr/) Cluster, and TUBITAK ULAKBIM Cluster ([TRUBA](https://www.truba.gov.tr/) resources).
