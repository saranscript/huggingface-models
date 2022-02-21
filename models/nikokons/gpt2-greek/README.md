---
language: el
---

## gpt2-greek
## Dataset: 
The model is trained on a collection of almost 5GB Greek texts, with the main source to be from Greek Wikipedia. The content is extracted using the Wikiextractor tool (Attardi, 2012). The dataset is constructed as 5 sentences per sample (about 3.7 millions of samples) and the end of document is marked with the string <|endoftext|> providing the model with paragraph information, as done for the original GPT-2 training set by Radford . The input sentences are pre-processed and tokenized using 22,000 merges of byte-pair encoding. 

## Model:
The model is the "small" version of GPT-2 (12-layer, 768-hidden, 12-heads) with the only difference that the maximum sequence length is set at 512 tokens instead of 1024.

## Training details: 
It is trained from scratch a generative Transformer model as GPT-2 on a large corpus of Greek text so that the model can generate long stretches of contiguous coherent text. Attention dropouts with a rate of 0.1 are used for regularization on all layers and L2 weight decay of 0,01. In addition, a batch size of 4 and accumulated gradients over 8 iterations are used, resulting in an effective batch size of 32. The model uses the Adam optimization scheme with a learning rate of 1e-4 and is trained for 20 epochs. The learning rate increases linearly from zero over the first 9000 updates and decreases linearly by using a linear schedule. The implementation is based on the open-source PyTorch-transformer library (HuggingFace 2019).

## Fine-tuned model using the pre-trained "gpt2-greek":
https://huggingface.co/nikokons/conversational-agent-el