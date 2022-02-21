---
language: en
pipeline_tag: fill-mask
---

### BERT (double)
Model and tokenizer files for BERT (double) model from [When Does Pretraining Help? Assessing Self-Supervised Learning for Law and the CaseHOLD Dataset](https://arxiv.org/abs/2104.08671).

### Training Data
BERT (double) is pretrained using the same English Wikipedia corpus that the base BERT model (uncased, 110M parameters), [bert-base-uncased](https://huggingface.co/bert-base-uncased), was pretrained on. For more information on the pretraining corpus, refer to the [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805) paper.

### Training Objective
This model is initialized with the base BERT model (uncased, 110M parameters), [bert-base-uncased](https://huggingface.co/bert-base-uncased), and trained for an additional 1M steps on the MLM and NSP objective. 

This facilitates a direct comparison to our BERT-based models for the legal domain, which are also pretrained for 2M total steps.
- Legal-BERT: zlucia/legalbert (https://huggingface.co/zlucia/legalbert)
- Custom Legal-BERT: zlucia/custom-legalbert (https://huggingface.co/zlucia/custom-legalbert)

### Usage
Please see the [casehold repository](https://github.com/reglab/casehold) for scripts that support computing pretrain loss and finetuning on BERT (double) for classification and multiple choice tasks described in the paper: Overruling, Terms of Service, CaseHOLD.

See `demo.ipynb` in the casehold repository for details on calculating domain specificity (DS) scores for tasks or task examples by taking the difference in pretrain loss on BERT (double) and Legal-BERT. DS score may be readily extended to estimate domain specificity of tasks in other domains using BERT (double) and existing pretrained models (e.g., [SciBERT](https://arxiv.org/abs/1903.10676)).

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

Lucia Zheng, Neel Guha, Brandon R. Anderson, Peter Henderson, and Daniel E. Ho. 2021. When Does Pretraining Help? Assessing Self-Supervised Learning for Law and the CaseHOLD Dataset. In *Proceedings of the 18th International Conference on Artificial Intelligence and Law (ICAIL '21)*, June 21-25, 2021, São Paulo, Brazil. ACM Inc., New York, NY, (in press). arXiv: [2104.08671 [cs.CL]](https://arxiv.org/abs/2104.08671).