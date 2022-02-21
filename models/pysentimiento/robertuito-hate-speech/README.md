---
language: 
  - es

tags:
  - twitter
  - hate-speech

---
# Hate Speech detection in Spanish
## robertuito-hate-speech

Repository: [https://github.com/pysentimiento/pysentimiento/](https://github.com/finiteautomata/pysentimiento/)



Model trained with SemEval 2019 Task 5: HatEval (SubTask B) corpus for Hate Speech detection in Spanish. Base model is [RoBERTuito](https://github.com/pysentimiento/robertuito), a RoBERTa model trained in Spanish tweets.

It is a multi-classifier model, with the following classes:

- **HS**: is it hate speech?
- **TR**: is it targeted to a specific individual?
- **AG**: is it aggressive?

## Results

Results for the four tasks evaluated in `pysentimiento`. Results are expressed as Macro F1 scores


| model         | emotion       | hate_speech   | irony         | sentiment     |
|:--------------|:--------------|:--------------|:--------------|:--------------|
| robertuito    | 0.560 ± 0.010 | 0.759 ± 0.007 | 0.739 ± 0.005 | 0.705 ± 0.003 |
| roberta       | 0.527 ± 0.015 | 0.741 ± 0.012 | 0.721 ± 0.008 | 0.670 ± 0.006 |
| bertin        | 0.524 ± 0.007 | 0.738 ± 0.007 | 0.713 ± 0.012 | 0.666 ± 0.005 |
| beto_uncased  | 0.532 ± 0.012 | 0.727 ± 0.016 | 0.701 ± 0.007 | 0.651 ± 0.006 |
| beto_cased    | 0.516 ± 0.012 | 0.724 ± 0.012 | 0.705 ± 0.009 | 0.662 ± 0.005 |
| mbert_uncased | 0.493 ± 0.010 | 0.718 ± 0.011 | 0.681 ± 0.010 | 0.617 ± 0.003 |
| biGRU         | 0.264 ± 0.007 | 0.592 ± 0.018 | 0.631 ± 0.011 | 0.585 ± 0.011 |


Note that for Hate Speech, these are the results for Semeval 2019, Task 5 Subtask B (HS+TR+AG detection)

## Citation

If you use this model in your research, please cite pysentimiento, RoBERTuito and HatEval papers:

```
% Pysentimiento
@misc{perez2021pysentimiento,
      title={pysentimiento: A Python Toolkit for Sentiment Analysis and SocialNLP tasks},
      author={Juan Manuel Pérez and Juan Carlos Giudici and Franco Luque},
      year={2021},
      eprint={2106.09462},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
% RoBERTuito paper
@misc{perez2021robertuito,
      title={RoBERTuito: a pre-trained language model for social media text in Spanish},
      author={Juan Manuel Pérez and Damián A. Furman and Laura Alonso Alemany and Franco Luque},
      year={2021},
      eprint={2111.09453},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
% HatEval paper

@inproceedings{hateval2019semeval,
  title={SemEval-2019 Task 5: Multilingual Detection of Hate Speech Against Immigrants and Women in Twitter},
  author={Basile, Valerio and Bosco, Cristina and Fersini, Elisabetta and Nozza, Debora and Patti, Viviana and Rangel, Francisco and Rosso, Paolo and Sanguinetti, Manuela},
  booktitle={Proceedings of the 13th International Workshop on Semantic Evaluation (SemEval-2019)},
  year={2019},
  publisher= {Association for Computational Linguistics}
}
```