---
language: tl
tags:
- gpt2
- tagalog
- filipino
license: gpl-3.0
inference: false
---

# GPT-2 Tagalog
The Tagalog GPT-2 model used to benchmark our fake news detection system Cruz et al. (2020). We make available an improved version of our GPT-2 model trained with NewsPH in addition to WikiText-TL-39.

## Limitations and Bias
The model was trained with two language modeling datasets for Tagalog:
* **WikiText-TL-39**, which is sourced from a dump of Tagalog WikiPedia.
* **NewsPH**, which is a dump of news articles from all available mainstream news outlets in the Philippines.

Due to the source of the training data, generated sentences out-of-the-box may sound and read like actual news articles, possessing the common tone and style of these works. While these may *look* like news articles, these are *not* news articles, and should not be read, understood, published, or shared as one. Language models do not inherently distinguish factual statements from non-factual ones, and as such, we discourage use of the model in systems and use-cases where the generated output is required to be true.

As this model is currently a prototype, bias was not thoroughly studied. Models inherit biases that are present in the data that they are trained with. Thing such as frequency of association of gender to occupation can induce certain biases in the model that will remain undetected unless thoroughly tested. As with the original GPT-2 model, we recommend that this model not be deployed or used in systems that interact with humans unless thorough study of potential biases is carried out.

We release this model with the intent that it may aid in the advancement of Filipino NLP, and that researchers and engineers who are interested in applying their work to the language may have a baseline model to use. For future work, in addition to the study of inherent bias, we mainly look into improving the quality of our models. As this is a prototype, a large-scale corpora was not used to train it. We plan to train larger GPT-2 models with larger corpora in the future.

## Citations

```bibtex
@inproceedings{localization2020cruz,
  title={{Localization of Fake News Detection via Multitask Transfer Learning}},
  author={Cruz, Jan Christian Blaise and Tan, Julianne Agatha and Cheng, Charibeth},
  booktitle={Proceedings of The 12th Language Resources and Evaluation Conference},
  pages={2589--2597},
  year={2020},
  url={https://www.aclweb.org/anthology/2020.lrec-1.315}
}
```

## Data and Other Resources
Data used to train this model as well as other benchmark datasets in Filipino can be found in my website at https://blaisecruz.com

## Contact
If you have questions, concerns, or if you just want to chat about NLP and low-resource languages in general, you may reach me through my work email at me@blaisecruz.com