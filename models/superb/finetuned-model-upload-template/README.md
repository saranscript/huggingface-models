# Fine-tuned Model Submission Template

This is a template reprository for the SUPERB benchmark for the _fine-tuned model_ category. In this category, participants are asked to fine-tuned a pretrained model in each of SUPERB's downstream tasks and then store the model weights and hyperparameters in this repo.

There are four steps involved in making a submission:

1. Fine-tune a pretrained model on a downstream task.
2. Implement the `PreTrainedModel` interface defined in each `model.py` module.
3. Store the weights and hyperparameters in the task directory
4. Push all the files to the Hugging Face Hub.