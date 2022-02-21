
---
language: 
- es
thumbnail: 
tags:
- simplification
- mt5
- spanish
license: cc-by-nc-sa-4.0
metrics:
- sari
widget:
- text: "La Simplificación Textual es el proceso de transformación de un texto a otro texto equivalente más comprensible para un determinado tipo de grupo o población."
- text: "Los textos simplificados son apropiados para muchos grupos de lectores, como, por ejemplo: estudiantes de idiomas, personas con discapacidades intelectuales y otras personas con necesidades especiales de lectura y comprensión.
"
---
# mt5-simplification-spanish

## Model description

This is a fine-tuned mt5-small model for generating simple text from complex text.

This model was created with the IXA Group research group of the University of the Basque Country, the model has been evaluated with the Sari, Bleu and Fklg metrics; it was trained and tested using the [Simplext corpus](https://dl.acm.org/doi/10.1145/2738046).

## Dataset

Simplext 

## Model Evaluation

Bleu: 13,186

Sari: 42,203

Fklg: 10,284


## Authors

Oscar M. Cumbicus-Pineda, Itziar Gonzalez-Dios, Aitor Soroa, November 2021

## Code

https://github.com/oskrmiguel/mt5-simplification