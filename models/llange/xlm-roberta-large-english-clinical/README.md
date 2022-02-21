# CLIN-X-EN: a pre-trained language model for the English clinical domain
Details on the model, the pre-training corpus and the downstream task performance are given in the paper: "CLIN-X: pre-trained language models and a study on cross-task transfer for concept extraction in the clinical domain" by Lukas Lange, Heike Adel, Jannik Strötgen and Dietrich Klakow. 
The paper can be found [here](https://arxiv.org/abs/2112.08754). 
In case of questions, please contact the authors as listed on the paper. 

Please cite the above paper when reporting, reproducing or extending the results.

    @misc{lange-etal-2021-clin-x,
          author    = {Lukas Lange and
                       Heike Adel and
                       Jannik Str{\"{o}}tgen and
                       Dietrich Klakow},
          title     = {CLIN-X: pre-trained language models and a study on cross-task transfer for concept extraction in the clinical domain},
          year={2021},
          eprint={2112.08754},
          archivePrefix={arXiv},
          primaryClass={cs.CL},
          url={https://arxiv.org/abs/2112.08754}
    }

## Training details
The model is based on the multilingual XLM-R transformer `(xlm-roberta-large)`, which was trained on 100 languages and showed superior performance in many different tasks across languages and can even outperform monolingual models in certain settings (Conneau et al. 2020). 
We train the CLIN-X model on clinical Pubmed abstracts (850MB) filtered
following Haynes et al. (2005). Pubmed is used with the courtesy of the U.S. National Library of Medicine

We initialize CLIN-X using the pre-trained XLM-R weights and train masked language modeling (MLM) on the Spanish clinical corpus for 3 epochs which roughly corresponds to 32k steps. This allows researchers and practitioners to address
the English clinical domain with an out-of-the-box tailored model. 

## Results for Spanish concept extraction
We apply CLIN-X-EN to five different English sequence labeling tasks from i2b2 in a standard sequence labeling architecture similar to Devlin et al. 2019 and compare to  BERT and ClinicalBERT. In addition, we perform experiments with an improved architecture `(+ OurArchitecture)` as described in the paper linked above. The code for our model architecture can be found [here](https://github.com/boschresearch/clin_x).

|                               | i2b2 2006 | i2b2 2010 | i2b2 2012 (Concept) | i2b2 2012 (Time) | i2b2 2014 |
|-------------------------------|-----------|-----------|---------------------|------------------|-----------|
| BERT                          | 94.80     | 82.25     | 76.51               | 75.28            | 94.86     |
| ClinicalBERT                  | 94.8      | 87.8      | 78.9                | 76.6             | 93.0      |
| CLIN-X (EN)                   | 96.25     | 88.10     | 79.58               | 77.70            | 96.73     |
| CLIN-X (EN) + OurArchitecture | **98.49** | **89.23** | **80.62**           | **78.50**        | **97.60** |

## Purpose of the project
This software is a research prototype, solely developed for and published as part of the publication cited above. It will neither be maintained nor monitored in any way.

## License
The CLIN-X models are open-sourced under the CC-BY 4.0 license. 
See the [LICENSE](LICENSE) file for details. 