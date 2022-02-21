# TE-for-Event-Extraction

## Model description

This is a TE model as part of the event extraction system in the ACL2021 paper: [Zero-shot Event Extraction via Transfer Learning: Challenges and Insights](https://aclanthology.org/2021.acl-short.42/). The pretrained architecture is [roberta-large](https://huggingface.co/roberta-large) and the fine-tuning data is [MNLI](https://cims.nyu.edu/~sbowman/multinli/).

The label mapping is:
```
LABEL_0: Contradiction
LABEL_1: Neutral
LABEL_2: Entailment
```

## Demo

To see how the model works, type a sentence and a hypothesis separated by "\<\/s\>\<\/s\>" in the right-hand-side textbox under "Hosted inference API".

Example:
- Input:
```
A car bomb exploded Thursday in a crowded outdoor market in the heart of Jerusalem. </s></s>  This text is about an attack.
```
- Output:
```
LABEL_2 (Entailment)
```

## Usage
- To use the TE model independently, follow the [huggingface documentation on AutoModelForSequenceClassification](https://huggingface.co/transformers/task_summary.html#sequence-classification).
- To use it as part of the event extraction system, please check out [our Github repo](https://github.com/veronica320/Zeroshot-Event-Extraction).


### BibTeX entry and citation info
```
@inproceedings{lyu-etal-2021-zero,
    title = "Zero-shot Event Extraction via Transfer Learning: {C}hallenges and Insights",
    author = "Lyu, Qing  and
      Zhang, Hongming  and
      Sulem, Elior  and
      Roth, Dan",
    booktitle = "Proceedings of the 59th Annual Meeting of the Association for Computational Linguistics and the 11th International Joint Conference on Natural Language Processing (Volume 2: Short Papers)",
    month = aug,
    year = "2021",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.acl-short.42",
    doi = "10.18653/v1/2021.acl-short.42",
    pages = "322--332",
    abstract = "Event extraction has long been a challenging task, addressed mostly with supervised methods that require expensive annotation and are not extensible to new event ontologies. In this work, we explore the possibility of zero-shot event extraction by formulating it as a set of Textual Entailment (TE) and/or Question Answering (QA) queries (e.g. {``}A city was attacked{''} entails {``}There is an attack{''}), exploiting pretrained TE/QA models for direct transfer. On ACE-2005 and ERE, our system achieves acceptable results, yet there is still a large gap from supervised approaches, showing that current QA and TE technologies fail in transferring to a different domain. To investigate the reasons behind the gap, we analyze the remaining key challenges, their respective impact, and possible improvement directions.",
}
```