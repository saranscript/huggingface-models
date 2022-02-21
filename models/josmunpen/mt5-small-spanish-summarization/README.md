
---
language: 
- es
thumbnail: 
tags:
- summarization
- mt5
- spanish
license: apache-2.0
datasets:
- larazonpublico
- es
metrics:
- rouge
widget:
- text: "La Guardia Civil ha desarticulado un grupo organizado dedicado a copiar en los examenes teoricos para la obtencion del permiso de conducir. Para ello, empleaban receptores y camaras de alta tecnologia y operaban desde la misma sede del Centro de examenes de la Direccion General de Trafico (DGT) en Mostoles. Es lo que han llamado la Operacion pinga.
El grupo desarticulado ofrecia el servicio de transporte y tecnologia para copiar y poder aprobar. Por dicho servicio cobraban 1.000 euros. Los investigadores sorprendieron in fraganti a una mujer intentando copiar en el examen. Portaba una chaqueta con dispositivos electronicos ocultos, concretamente un telefono movil al que estaba conectada una camara que habia sido insertada en la parte frontal de la chaqueta para transmitir online el examen y que orientada al ordenador del Centro de Examenes en el que aparecen las preguntas, permitia visualizar las imagenes en otro ordenador alojado en el interior de un vehiculo estacionado en las inmediaciones del centro. En este vehiculo, se encontraban el resto del grupo desarticulado con varios ordenadores portatiles y tablets abiertos y conectados a paginas de test de la DGT para consultar las respuestas. Estos, comunicaban con la mujer que estaba en el aula haciendo el examen a traves de un diminuto receptor bluetooth que portaba en el interior de su oido. 
Luis de Lama, portavoz de la Guardia Civil de Trafico destaca que los ciudadanos, eran de origen chino, y copiaban en el examen utilizando la tecnologia facilitada por una organizacion. Destaca que, ademas de parte del fraude que supone copiar en un examen muchos de estos ciudadanos desconocian el idioma, no hablan ni entienden el español lo que supone un grave riesgo para la seguridad vial por desconocer las señales y letreros que avisan en carretera de muchas incidencias.
"
---
# mt5-small-spanish-summarization

## Model description

This is a mt5-small model finetuned for generating headlines from the body of the news in Spanish. 

## Training data

The model was trained with 58425 news extracted from the La Razón (31477) and Público (26948) newspapers. These news belong to the following categories: "España", "Cultura", "Economía", "Igualdad" and "Política".

## Training procedure

It was trained with Google Colab's GPU Tesla P100-PCIE-16GB for 2 epochs.

### Hyperparameters

{evaluation_strategy = "epoch",
learning_rate = 2e-4,
per_device_train_batch_size = 6,
per_device_eval_batch_size = 6,
weight_decay = 0.01,
save_total_limi t= 3,
num_train_epochs = 2,
predict_with_generate = True,
fp16 = False}


## Eval results
| metric | score |
| --- | ----- |
| rouge1 | 44.03 |
| rouge2 | 28.2900 |
| rougeL | 40.54 |
| rougeLsum | 40.5587 |


### BibTeX entry and citation info

```bibtex
@inproceedings{ mt5lrpjosmunpen,
  year={2020},

}
```