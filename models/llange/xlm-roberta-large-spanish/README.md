# Spanish XLM-R (from NLNDE-MEDDOPROF)
This Spanish language model was created for the MEDDOPROF shared task as part of the **NLNDE** team submission and outperformed all other participants in both sequence labeling tasks. 

Details on the model, the pre-training corpus and the downstream task performance are given in the paper: "Boosting Transformers for Job Expression Extraction and Classification in a Low-Resource Setting" by Lukas Lange, Heike Adel and Jannik Strötgen. 
The paper can be found [here](http://ceur-ws.org/Vol-2943/meddoprof_paper1.pdf). 
In case of questions, please contact the authors as listed on the paper. 

Please cite the above paper when reporting, reproducing or extending the results.

    @inproceedings{lange-etal-2021-meddoprof,
      author    = {Lukas Lange and
                   Heike Adel and
                   Jannik Str{\"{o}}tgen},
      title     = {Boosting Transformers for Job Expression Extraction and Classification in a Low-Resource Setting},
      year={2021},
      booktitle= {{Proceedings of The Iberian Languages Evaluation Forum (IberLEF 2021)}},
      series = {{CEUR} Workshop Proceedings},
      url = {http://ceur-ws.org/Vol-2943/meddoprof_paper1.pdf},
	}


## Training details
We use XLM-R (`xlm-roberta-large`, Conneau et al. 2020) as the main component of our models. XLM-R is a pretrained multilingual transformer model for 100 languages, including Spanish. It shows superior performance in different tasks across languages, and can even outperform
monolingual models in certain settings. It was pretrained on a large-scale corpus,
and Spanish documents made up only 2% of this data.
Thus, we explore further pretraining of this model and tune it towards Spanish
documents by pretraining a medium-size Spanish corpus with general
domain documents. For this, we use the [spanish corpus](https://github.com/josecannete/spanish-corpora) used to train the BETO model. 

We use masked language modeling for pretraining and trained for three epochs
over the corpus, which roughly corresponds to 685k steps using a batch-size of 4.

## Performance
This model was trained in the context of the Meddoprof shared tasks and outperformed all other participants in both sequence labeling tasks. Our results (F1) in comparison with the standard XLM-R and the second-best system of the shared task are given in the Table. 
More information on the shared task and other participants is given in this paper [here](http://journal.sepln.org/sepln/ojs/ojs/index.php/pln/article/view/6393/3813). 
The code for our NER models can be found [here](https://github.com/boschresearch/nlnde-meddoprof). 

|                                 | Meddoprof Task 1 (NER) | Meddoprof Task 2 (CLASS) |
|---------------------------------|------------------------|--------------------------|
| Second-best System              | 80.0                   | 76.4                     |
| XLM-R (our baseline)            | 79.2                   | 77.6                     |
| Our Spanish XLM-R (best System) | **83.2**               | **79.1**                 |

## Purpose of the project
This software is a research prototype, solely developed for and published as part of the publication cited above. It will neither be maintained nor monitored in any way.

## License
The CLIN-X models are open-sourced under the CC-BY 4.0 license. 
See the [LICENSE](LICENSE) file for details. 