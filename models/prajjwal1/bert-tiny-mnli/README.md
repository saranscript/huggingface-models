The following model is a Pytorch pre-trained model obtained from converting Tensorflow checkpoint found in the [official Google BERT repository](https://github.com/google-research/bert). These BERT variants were introduced in the paper [Well-Read Students Learn Better: On the Importance of Pre-training Compact Models](https://arxiv.org/abs/1908.08962). These models are trained on MNLI.

If you use the model, please consider citing the paper
```
@misc{bhargava2021generalization,
      title={Generalization in NLI: Ways (Not) To Go Beyond Simple Heuristics}, 
      author={Prajjwal Bhargava and Aleksandr Drozd and Anna Rogers},
      year={2021},
      eprint={2110.01518},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```
Original Implementation and more info can be found in [this Github repository](https://github.com/prajjwal1/generalize_lm_nli).

```
MNLI: 60%
MNLI-mm: 61.61%
```
These models were trained for 4 epochs.

[@prajjwal_1](https://twitter.com/prajjwal_1)
