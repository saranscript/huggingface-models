---
language: en
license: apache-2.0
datasets:
- glue
---
# Bert-base-cased Fine Tuned Glue Mrpc Demo

This checkpoint was initialized from the pre-trained checkpoint bert-base-cased and subsequently fine-tuned on GLUE task: mrpc using [this](https://colab.research.google.com/drive/162pW3wonGcMMrGxmA-jdxwy1rhqXd90x?usp=sharing) notebook.
Training was conducted for 3 epochs, using a linear decaying learning rate of 2e-05, and a total batch size of 32.

The model has a final training loss of 0.103 and a accuracy of 0.831.