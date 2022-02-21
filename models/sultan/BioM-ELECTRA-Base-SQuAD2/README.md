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

We fine-tuned BioM-ELECTRA-Base, which was pre-trained on PubMed Abstracts, on the SQuAD2.0 dataset. Fine-tuning the biomedical language model on the SQuAD dataset helps improve the score on the BioASQ challenge. If you plan to work with BioASQ or biomedical QA tasks, it's better to use this model over BioM-ELECTRA-Base. 

Huggingface library doesn't implement Layer-Wise decay feature, which affects the performance on SQuAD task. The reported result of BioM-ELECTRA-Base-SQuAD in our paper is 84.4 (F1) since we use ELECTRA open-source code with TF checkpoint, which uses Layer-Wise decay. You can downoad our TensorFlow checkpoint that was fine-tuned on SQuAD2.0 and achieved 84.4 F1 score from here https://github.com/salrowili/BioM-Transformers .


Evaluation results on SQuAD2.0 Dev Dataset
```
  eval_HasAns_exact      = 79.2679
  eval_HasAns_f1         = 86.5416
  eval_HasAns_total      =    5928
  eval_NoAns_exact       = 75.8789
  eval_NoAns_f1          = 75.8789
  eval_NoAns_total       =    5945
  eval_best_exact        =  77.571
  eval_best_exact_thresh =     0.0
  eval_best_f1           = 81.2026
  eval_best_f1_thresh    =     0.0
  eval_exact             =  77.571
  eval_f1                = 81.2026
  eval_samples           =   11979
  eval_total             =   11873

```


- First make sure to install all libraries on Google Colab and make sure GPU is enabled

```python
!git  clone https://github.com/huggingface/transformers
!pip3 install -e transformers
!pip3 install sentencepiece
!pip3 install -r /content/transformers/examples/pytorch/question-answering/requirements.txt

```

- Training script

```python
python3 transformers/examples/pytorch/question-answering/run_qa.py --model_name_or_path sultan/BioM-ELECTRA-Base-Discriminator \
--dataset_name squad_v2 \
--do_train \
--do_eval \
--dataloader_num_workers 20 \
--preprocessing_num_workers 20 \
--version_2_with_negative \
--num_train_epochs 3 \
--learning_rate 4e-5 \
--max_seq_length 512 \
--doc_stride 128 \
--per_device_train_batch_size 8 \
--gradient_accumulation_steps 3 \
--per_device_eval_batch_size 128 \
--fp16 \
--fp16_opt_level O1 \
--logging_steps 50 \
--save_steps 5000 \
--overwrite_output_dir \
--output_dir out
```


- Reproduce results without training ( only eval):

```python
python transformers/examples/pytorch/question-answering/run_qa.py --model_name_or_path sultan/BioM-ELECTRA-Base-SQuAD2 \
--do_eval \
--version_2_with_negative \
--per_device_eval_batch_size 8 \
--dataset_name squad_v2 \
--overwrite_output_dir \
--fp16 \
--output_dir out
```

- You don't need to download the SQuAD2 dataset. The code will download it from the HuggingFace datasets hub.
- Check our GitHub repo at https://github.com/salrowili/BioM-Transformers for TensorFlow and GluonNLP checkpoints. 


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