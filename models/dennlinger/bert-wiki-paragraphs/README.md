# BERT-Wiki-Paragraphs

Authors: Satya Almasian\*, Dennis Aumiller\*, Lucienne-Sophie Marmé, Michael Gertz  
Contact us at `<lastname>@informatik.uni-heidelberg.de`  
Details for the training method can be found in our work [Structural Text Segmentation of Legal Documents](https://arxiv.org/abs/2012.03619).
The training procedure follows the same setup, but we substitute legal documents for Wikipedia in this model.

Training is performed in a form of weakly-supervised fashion to determine whether paragraphs topically belong together or not.
We utilize automatically generated samples from Wikipedia for training, where paragraphs from within the same section are assumed to be topically coherent.  
We use the same articles as ([Koshorek et al., 2018](https://arxiv.org/abs/1803.09337)), 
albeit from a 2021 dump of Wikpeida, and split at paragraph boundaries instead of the sentence level.

## Training Setup
The model was trained for 3 epochs from `bert-base-uncased` on paragraph pairs (limited to 512 subwork with the `longest_first` truncation strategy).
We use a batch size of 24 wit 2 iterations gradient accumulation (effective batch size of 48), and a learning rate of 1e-4, with gradient clipping at 5.
Training was performed on a single Titan RTX GPU over the duration of 3 weeks.
