---

language:
- en
tags:
- text-generation
- gpt2
- gpt
license: mit
datasets:
- natural questions

widget:
- text: "Do you like my new haircut?\nperson beta:\n\n"  
  example_title: "haircut"
- text: "I love to learn new things.. are you willing to teach me something?\nperson beta:\n\n"  
  example_title: "teaching"
- text: "What's your favorite animal? Mine is the dog? \nperson beta:\n\n"
  example_title: "favorite"
- text: "how much does it cost?\nperson beta:\n\n"
  example_title: "money"

inference:
  parameters:
    min_length: 2
    max_length: 64
    length_penalty: 0.6
    no_repeat_ngram_size: 3
    do_sample: True
    top_p: 0.85
    top_k: 10
    repetition_penalty: 2.1
    

---
# ai-msgbot GPT2-XL

_NOTE: model card is WIP_

GPT2-XL (~1.5 B parameters) trained on [the Wizard of Wikipedia dataset](https://parl.ai/projects/wizard_of_wikipedia/) for 40k steps with **33**/36 layers frozen using `aitextgen`. 


Designed for use with [ai-msgbot](https://github.com/pszemraj/ai-msgbot) to create an open-ended chatbot (of course, if other use cases arise, have at it).


## conversation data

The dataset was tokenized and fed to the model as a conversation between two speakers, whose names are below. This is relevant for writing prompts and filtering/extracting text from responses.

`script_speaker_name` = `person alpha`

`script_responder_name` = `person beta`

## examples

- the default inference API examples should work _okay_
- an ideal test would be explicitly adding `person beta` into the prompt text the model is forced to respond to instead of adding onto the entered prompt.

### Example prompt:

```
do you like to eat beans? 

person beta:
```

### Resulting output

```
do you like to eat beans?person beta:
yes, i like fried beans.

person alpha:
i wonder when the first beans were cultivated and how they were processed.

person beta:
nitrogenic bacteria (in
```

_Note: the Inference API cuts off generation due to length, if run elsewhere you would see what comes after "(in"_

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