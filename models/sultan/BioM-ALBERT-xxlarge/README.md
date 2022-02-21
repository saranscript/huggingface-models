# BioM-Transformers: Building Large Biomedical Language Models with BERT, ALBERT and ELECTRA

# Abstract


The impact of design choices on the performance
of biomedical language models recently
has been a subject for investigation. In
this paper, we empirically study biomedical
domain adaptation with large transformer models
using different design choices. We evaluate
the performance of our pretrained models
against other existing biomedical language
models in the literature. Our results show that
we achieve state-of-the-art results on several
biomedical domain tasks despite using similar
or less computational cost compared to other
models in the literature. Our findings highlight
the significant effect of design choices on
improving the performance of biomedical language
models.

# Model Description
This model was pre-trained on PubMed Abstracts only with biomedical domain vocabulary for 264K steps with a batch size of 8192 on TPUv3-512 unit. In order to help researchers with limited resources to fine-tune larger models, we created an example with PyTorch XLA. PyTorch XLA (https://github.com/pytorch/xla) is a library that allows you to use PyTorch on TPU units, which is provided for free by Google Colab and Kaggle. Follow this example to work with PyTorch/XLA [Link](https://github.com/salrowili/BioM-Transformers/blob/main/examples/Fine_Tuning_Biomedical_Models_on_Text_Classification_Task_With_HuggingFace_Transformers_and_PyTorch_XLA.ipynb)

Check our GitHub repo at https://github.com/salrowili/BioM-Transformers for TensorFlow and GluonNLP checkpoints. We also updated this repo with a couple of examples on how to fine-tune LMs on text classification and questions answering tasks such as ChemProt, SQuAD, and BioASQ.

# Colab Notebook Examples


BioM-ELECTRA-LARGE on NER and ChemProt Task [![Open In Colab][COLAB]](https://colab.research.google.com/github/salrowili/BioM-Transformers/blob/main/examples/Example_of_NER_and_ChemProt_Task_on_TPU.ipynb)

BioM-ELECTRA-Large on SQuAD2.0 and BioASQ7B Factoid tasks [![Open In Colab][COLAB]](https://colab.research.google.com/github/salrowili/BioM-Transformers/blob/main/examples/Example_of_SQuAD2_0_and_BioASQ7B_tasks_with_BioM_ELECTRA_Large_on_TPU.ipynb)

BioM-ALBERT-xxlarge on SQuAD2.0 and BioASQ7B Factoid tasks [![Open In Colab][COLAB]](https://colab.research.google.com/github/salrowili/BioM-Transformers/blob/main/examples/Example_of_SQuAD2_0_and_BioASQ7B_tasks_with_BioM_ALBERT_xxlarge_on_TPU.ipynb)

Text Classification Task With HuggingFace Transformers and PyTorchXLA on Free TPU [![Open In Colab][COLAB]](https://colab.research.google.com/github/salrowili/BioM-Transformers/blob/main/examples/Fine_Tuning_Biomedical_Models_on_Text_Classification_Task_With_HuggingFace_Transformers_and_PyTorch_XLA.ipynb)



[COLAB]: https://colab.research.google.com/assets/colab-badge.svg
# Acknowledgment

We would like to acknowledge the support we have from Tensorflow Research Cloud (TFRC) team to grant us access to TPUv3 units.

# Citation 

```bibtex
@inproceedings{alrowili-shanker-2021-biom,
title = "{B}io{M}-Transformers: Building Large Biomedical Language Models with {BERT}, {ALBERT} and {ELECTRA}",
author = "Alrowili, Sultan and
Shanker, Vijay",
booktitle = "Proceedings of the 20th Workshop on Biomedical Language Processing",
month = jun,
year = "2021",
address = "Online",
publisher = "Association for Computational Linguistics",
url = "https://www.aclweb.org/anthology/2021.bionlp-1.24",
pages = "221--227",
abstract = "The impact of design choices on the performance of biomedical language models recently has been a subject for investigation. In this paper, we empirically study biomedical domain adaptation with large transformer models using different design choices. We evaluate the performance of our pretrained models against other existing biomedical language models in the literature. Our results show that we achieve state-of-the-art results on several biomedical domain tasks despite using similar or less computational cost compared to other models in the literature. Our findings highlight the significant effect of design choices on improving the performance of biomedical language models.",
}
```