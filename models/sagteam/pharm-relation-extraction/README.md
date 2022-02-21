pharm-relation-extraction
===
Model trained to recognize 4 types of relationships between significant pharmacological entities in russian-language reviews: ADR–Drugname, Drugname–Diseasename, Drugname–SourceInfoDrug, Diseasename–Indication. The input of the model is a review text and a pair of entities, between which it is required to determine the fact of a relationship and one of the 4 types of relationship, listed above.

Data
----
Proposed model is trained on a subset of 908 reviews of the [Russian Drug Review Corpus (RDRS)](https://arxiv.org/pdf/2105.00059.pdf). The subset contains the pairs of entities marked with the 4 listed types of relationships:
- ADR-Drugname — the relationship between the drug and its side effects
- Drugname-SourceInfodrug — the relationship between the medication and the source of information about it (e.g., “was advised at the pharmacy”, e.g., “was advised at the pharmacy”, “the doctor recommended it”); 
- Drugname-Diseasname — the relationship between the drug and the disease
- Diseasename-Indication — the connection between the illness and its symptoms (e.g., “cough”, “fever 39 degrees”)
Also, this subset contains pairs of the same entity types between which there is no relationship: for example, a drug and an unrelated side effect that appeared after taking another drug; in other words, this side effect is related to another drug.

Model topology and training
----
Proposed model is based on the  [XLM-RoBERTA-large](https://arxiv.org/abs/1911.02116) topology. After the additional training as a language model on corpus of unmarked drug reviews, this model was trained as a classification model on 80% of the texts from subset of the corps described above.

How to use
----
See section "How to use" in [our git repository for the model](https://github.com/sag111/Relation_Extraction)

Results
----
Here are the accuracy, estimated by the f1 score metric for the recognition of relationships on the best fold.

| ADR–Drugname  | Drugname–Diseasename | Drugname–SourceInfoDrug | Diseasename–Indication |
| ------------- | -------------------- | ----------------------- | ---------------------- |
| 0.955         | 0.892                | 0.922                   | 0.891                  |


Citation info
----
If you have found our results helpful in your work, feel free to cite our publication as:

```
@article{sboev2021extraction,
  title={Extraction of the Relations between Significant Pharmacological Entities in Russian-Language Internet Reviews on Medications},
  author={Sboev, Alexander and Selivanov, Anton and Moloshnikov, Ivan and Rybka, Roman and Gryaznov, Artem and Sboeva, Sanna and Rylkov, Gleb},
  year={2021},
  publisher={Preprints}
}
```