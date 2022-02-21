# OpenVINO model bert-large-uncased-whole-word-masking-squad-int8-0001

This is a BERT-large model pre-trained on lower-cased English text using Whole-Word-Masking and fine-tuned on the SQuAD v1.1 training set. The model performs question answering for English language; the input is a concatenated premise and question for the premise, and the output is the location of the answer to the question inside the premise. For details about the original floating-point model, check out [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805).

The model has been further quantized to INT8 precision using quantization-aware fine-tuning with [NNCF](https://github.com/openvinotoolkit/nncf).

Model source: [Open Model Zoo](https://github.com/openvinotoolkit/open_model_zoo/tree/master/models/intel/bert-large-uncased-whole-word-masking-squad-int8-0001)