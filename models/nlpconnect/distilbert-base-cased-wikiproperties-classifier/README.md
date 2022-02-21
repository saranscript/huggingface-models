      {'author': 'P50',
       'capital': 'P36',
       'child': 'P40',
       'country': 'P17',
       'country of origin': 'P495',
       'creator': 'P170',
       'educated at': 'P69',
       'founder': 'P112',
       'genre': 'P136',
       'headquarters location': 'P159',
       'language of work or name': 'P407',
       'located in the administrative territorial entity': 'P131',
       'location': 'P276',
       'location of formation': 'P740',
       'manufacturer': 'P176',
       'notable work': 'P800',
       'occupation': 'P106',
       'owned by': 'P127',
       'performer': 'P175',
       'place of birth': 'P19',
       'place of death': 'P20',
       'position played on team / speciality': 'P413',
       'record label': 'P264',
       'spouse': 'P26'}
       
       1250/1250 [==============================] - 159s 116ms/step - loss: 0.2096 - accuracy: 0.9570 - val_loss: 0.0407 - val_accuracy: 0.9805
       
       
       from transformers import pipeline
       classfier = pipeline("text-classification", model="nlpconnect/distilbert-base-cased-wikiproperties-classifier")