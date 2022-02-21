---
language: en
pipeline_tag: fill-mask
tags:
- legal
---

###  Legal-BERT
Model and tokenizer files for Legal-BERT model from [When Does Pretraining Help? Assessing Self-Supervised Learning for Law and the CaseHOLD Dataset of 53,000+ Legal Holdings](https://arxiv.org/abs/2104.08671).

### Training Data
The pretraining corpus was constructed by ingesting the entire Harvard Law case corpus from 1965 to the present (https://case.law/). The size of this corpus (37GB) is substantial, representing 3,446,187 legal decisions across all federal and state courts, and is larger than the size of the BookCorpus/Wikipedia corpus originally used to train BERT (15GB).

### Training Objective
This model is initialized with the base BERT model (uncased, 110M parameters), [bert-base-uncased](https://huggingface.co/bert-base-uncased), and trained for an additional 1M steps on the MLM and NSP objective, with tokenization and sentence segmentation adapted for legal text (cf. the paper).

### Usage
Please see the [casehold repository](https://github.com/reglab/casehold) for scripts that support computing pretrain loss and finetuning on Legal-BERT for classification and multiple choice tasks described in the paper: Overruling, Terms of Service, CaseHOLD.

### Citation
	@inproceedings{zhengguha2021,
			title={When Does Pretraining Help? Assessing Self-Supervised Learning for Law and the CaseHOLD Dataset},
			author={Lucia Zheng and Neel Guha and Brandon R. Anderson and Peter Henderson and Daniel E. Ho},
			year={2021},
			eprint={2104.08671},
			archivePrefix={arXiv},
			primaryClass={cs.CL},
			booktitle={Proceedings of the 18th International Conference on Artificial Intelligence and Law},
			publisher={Association for Computing Machinery}
	}

Lucia Zheng, Neel Guha, Brandon R. Anderson, Peter Henderson, and Daniel E. Ho. 2021. When Does Pretraining Help? Assessing Self-Supervised Learning for Law and the CaseHOLD Dataset. In *Proceedings of the 18th International Conference on Artificial Intelligence and Law (ICAIL '21)*, June 21-25, 2021,  São Paulo, Brazil. ACM Inc., New York, NY, (in press). arXiv: [2104.08671 \\[cs.CL\\]](https://arxiv.org/abs/2104.08671).
