# ai-msgbot GPT2-L

_NOTE: model card is WIP_

GPT2-L (774M parameters) trained on [the Wizard of Wikipedia dataset](https://parl.ai/projects/wizard_of_wikipedia/) for 40k steps with 34/36 layers frozen using `aitextgen`. 


Designed for use with [ai-msgbot](https://github.com/pszemraj/ai-msgbot) to create an open-ended chatbot (of course, if other use cases arise have at it).


## conversation data

The dataset was tokenized and fed to the model as a conversation between two speakers, whose names are below. this is relevant for writing prompts and filtering/extracting text from responses.

`script_speaker_name` = `person alpha`

`script_responder_name` = `person beta`


## examples

- the default inference API examples should work _okay_
- an ideal test would be explicitly adding `person beta` to the **end** of the prompt text. The model is forced to respond to the entered chat prompt instead of adding to the entered prompt and then responding to that (which may cut off the response text due to the Inference API limits).

## citations 
```
@inproceedings{dinan2019wizard,
  author={Emily Dinan and Stephen Roller and Kurt Shuster and Angela Fan and Michael Auli and Jason Weston},
  title={{W}izard of {W}ikipedia: Knowledge-powered Conversational Agents},
  booktitle = {Proceedings of the International Conference on Learning Representations (ICLR)},
  year={2019},
}

@inproceedings{li-etal-2017-dailydialog,
    title = "{D}aily{D}ialog: A Manually Labelled Multi-turn Dialogue Dataset",
    author = "Li, Yanran  and
      Su, Hui  and
      Shen, Xiaoyu  and
      Li, Wenjie  and
      Cao, Ziqiang  and
      Niu, Shuzi",
    booktitle = "Proceedings of the Eighth International Joint Conference on Natural Language Processing (Volume 1: Long Papers)",
    month = nov,
    year = "2017",
    address = "Taipei, Taiwan",
    publisher = "Asian Federation of Natural Language Processing",
    url = "https://aclanthology.org/I17-1099",
    pages = "986--995",
    abstract = "We develop a high-quality multi-turn dialog dataset, \textbf{DailyDialog}, which is intriguing in several aspects. The language is human-written and less noisy. The dialogues in the dataset reflect our daily communication way and cover various topics about our daily life. We also manually label the developed dataset with communication intention and emotion information. Then, we evaluate existing approaches on DailyDialog dataset and hope it benefit the research field of dialog systems. The dataset is available on \url{http://yanran.li/dailydialog}",
}
```