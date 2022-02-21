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

This model is fine-tuned on the SQuAD2.0 dataset. Fine-tuning the biomedical language model on the SQuAD dataset helps improve the score on the BioASQ challenge. If you plan to work with BioASQ or biomedical QA tasks, it's better to use this model over BioM-ALBERT-xxlarge. This model (TensorFlow version ) took the lead in the BioASQ9b-Factoid challenge under the name of (UDEL-LAB1). 

If you want to try our Tensor Flow example and how to fine-tune ALBERT on SQuAD and BioASQ follow this link :

https://github.com/salrowili/BioM-Transformers/blob/main/examples/Example_of_SQuAD2_0_and_BioASQ7B_tasks_with_BioM_ALBERT_xxlarge_on_TPU.ipynb

To see the full details of BioASQ9B results, please check this link http://participants-area.bioasq.org/results/9b/phaseB/ ( you need to register).

Huggingface library doesn't implement the Layer-Wise decay feature, which affects the performance on the SQuAD task. The reported result of BioM-ALBERT-xxlarge-SQuAD in our paper is 87.00 (F1) since we use ALBERT open-source code with TF checkpoint, which uses Layer-Wise decay. 

Result with PyTorch and V100 GPU

```
***** eval metrics *****
HasAns_exact      = 77.6484
HasAns_f1         = 85.0136
HasAns_total      =    5928
NoAns_exact       =  86.577
NoAns_f1          =  86.577
NoAns_total       =    5945
best_exact        = 82.1191
best_exact_thresh =     0.0
best_f1           = 85.7964
best_f1_thresh    =     0.0
eval_samples      =   12551
exact             = 82.1191
f1                = 85.7964
total             =   11873
```

To reproduce results in Google Colab:

- Make sure you have GPU enabled.

- Clone and install required libraries through this code

!git  clone https://github.com/huggingface/transformers

!pip3 install -e transformers

!pip3 install sentencepiece

!pip3 install -r /content/transformers/examples/pytorch/question-answering/requirements.txt

- Run this python code:

```python
python /content/transformers/examples/pytorch/question-answering/run_qa.py --model_name_or_path BioM-ALBERT-xxlarge-SQuAD2 \
--do_eval \
--version_2_with_negative \
--per_device_eval_batch_size 8 \
--dataset_name squad_v2 \
--overwrite_output_dir \
--fp16 \
--output_dir out
```

You don't need to download the SQuAD2 dataset. The code will download it from the HuggingFace datasets hub.

Check our GitHub repo at https://github.com/salrowili/BioM-Transformers for TensorFlow and GluonNLP checkpoints.

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