# Model Overview
This is an ELECTRA-Large QA Model trained from https://huggingface.co/google/electra-large-discriminator in two stages. First, it is trained on synthetic adversarial data generated using a BART-Large question generator, and then it is trained on SQuAD and AdversarialQA (https://arxiv.org/abs/2002.00293) in a second stage of fine-tuning.

# Data
Training data: SQuAD + AdversarialQA
Evaluation data: SQuAD + AdversarialQA

# Training Process
Approx. 1 training epoch on the synthetic data and 2 training epochs on the manually-curated data.

# Additional Information
Please refer to https://arxiv.org/abs/2104.08678 for full details. You can interact with the model on Dynabench here: https://dynabench.org/models/109