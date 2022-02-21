# Demo

Please try this [➤➤➤ Colab Notebook Demo (click me!)](https://colab.research.google.com/drive/1cAtfkbhqsRsT59y3imjR1APw3MHDMkuV?usp=sharing)

| Context | Response | `human_vs_rand` score |
| :------ | :------- | :------------: |
| I love NLP! | He is a great basketball player. | 0.027 |
| I love NLP! | Can you tell me how it works? | 0.754 |
| I love NLP! | Me too! | 0.631 |

The `human_vs_rand` score predicts how likely the response is corresponding to the given context, rather than a random response.


# DialogRPT-human-vs-rand

### Dialog Ranking Pretrained Transformers

> How likely a dialog response is upvoted 👍 and/or gets replied 💬? 

This is what [**DialogRPT**](https://github.com/golsun/DialogRPT) is learned to predict.
It is a set of dialog response ranking models proposed by [Microsoft Research NLP Group](https://www.microsoft.com/en-us/research/group/natural-language-processing/) trained on 100 + millions of human feedback data. 
It can be used to improve existing dialog generation model (e.g., [DialoGPT](https://huggingface.co/microsoft/DialoGPT-medium)) by re-ranking the generated response candidates.

Quick Links:
* [EMNLP'20 Paper](https://arxiv.org/abs/2009.06978/)
* [Dataset, training, and evaluation](https://github.com/golsun/DialogRPT)
* [Colab Notebook Demo](https://colab.research.google.com/drive/1cAtfkbhqsRsT59y3imjR1APw3MHDMkuV?usp=sharing)

We considered the following tasks and provided corresponding pretrained models.

|Task | Description  | Pretrained model |
| :------------- | :----------- | :-----------: |
|  **Human feedback**  |  **given a context and its two human responses, predict...**|
| `updown` |  ... which gets more upvotes? | [model card](https://huggingface.co/microsoft/DialogRPT-updown) |
| `width`| ... which gets more direct replies?  | [model card](https://huggingface.co/microsoft/DialogRPT-width) |
| `depth`|  ... which gets longer follow-up thread?  | [model card](https://huggingface.co/microsoft/DialogRPT-depth) |
|  **Human-like** (human vs fake) | **given a context and one human response, distinguish it with...** |
| `human_vs_rand`| ... a random human response  | this model |
| `human_vs_machine`| ... a machine generated response  | [model card](https://huggingface.co/microsoft/DialogRPT-human-vs-machine) |



### Contact:
Please create an issue on [our repo](https://github.com/golsun/DialogRPT)

### Citation:
```
@inproceedings{gao2020dialogrpt,
    title={Dialogue Response RankingTraining with Large-Scale Human Feedback Data},
    author={Xiang Gao and Yizhe Zhang and Michel Galley and Chris Brockett and Bill Dolan},
    year={2020},
    booktitle={EMNLP}
}
```
