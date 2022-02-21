---
language:
- es
license: apache-2.0
tags:
- legal
- spanish
datasets:
- legal_ES
- temu_legal  
metrics:
- ppl
widget:
- text: "La ley fue <mask> finalmente." 
- text: "El Tribunal <mask> desestimó el recurso de amparo."
- text: "Hay base legal dentro del marco <mask> actual."

---
# Spanish Legal-domain RoBERTa

There are few models trained for the Spanish language. Some of the models have been trained with a low resource, unclean corpora. The ones derived from the Spanish National Plan for Language Technologies are proficient solving several tasks and have been trained using large scale clean corpora. However, the Spanish Legal domain language could be think of an independent language on its own. We therefore created a Spanish Legal model from scratch trained exclusively on legal corpora.

## Citing 
```
@misc{gutierrezfandino2021legal,
      title={Spanish Legalese Language Model and Corpora}, 
      author={Asier Gutiérrez-Fandiño and Jordi Armengol-Estapé and Aitor Gonzalez-Agirre and Marta Villegas},
      year={2021},
      eprint={2110.12201},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

For more information visit our [GitHub repository](https://github.com/PlanTL-GOB-ES/lm-legal-es)

## Funding
This work was funded by the Spanish State Secretariat for Digitalization and Artificial Intelligence (SEDIA) within the framework of the Plan-TL.

## Disclaimer

The models published in this repository are intended for a generalist purpose and are available to third parties. These models may have bias and/or any other undesirable distortions.

When third  parties, deploy or provide systems and/or services to other parties using any of these models (or using systems based on these models) or become users of the models, they should note that it is their responsibility to mitigate the risks arising from their use and, in any event, to comply with applicable regulations, including regulations regarding the use of artificial intelligence.

In no event shall the owner of the models (SEDIA – State Secretariat for digitalization and artificial intelligence) nor the creator (BSC – Barcelona Supercomputing Center) be liable for any results arising from the use made by third parties of these models.

 

 

Los modelos publicados en este repositorio tienen una finalidad generalista y están a disposición de terceros. Estos modelos pueden tener sesgos y/u otro tipo de distorsiones indeseables.

Cuando terceros desplieguen o proporcionen sistemas y/o servicios a otras partes usando alguno de estos modelos (o utilizando sistemas basados en estos modelos) o se conviertan en usuarios de los modelos, deben tener en cuenta que es su responsabilidad mitigar los riesgos derivados de su uso y, en todo caso, cumplir con la normativa aplicable, incluyendo la normativa en materia de uso de inteligencia artificial.

En ningún caso el propietario de los modelos (SEDIA – Secretaría de Estado de Digitalización e Inteligencia Artificial) ni el creador (BSC – Barcelona Supercomputing Center) serán responsables de los resultados derivados del uso que hagan terceros de estos modelos.