## Title Generator
References this [notebook](https://shivanandroy.com/transformers-generating-arxiv-papers-title-from-abstracts/)

Using `t5-small`, trained on a batch size of 16 for 4 epochs, utilising the ArXiV dataset through the `SimpleTransformers` library. Around 15k data was used for training and 3.7k data for evaluation.

This is a `.pkl` file.

### Prerequisites
Install `simpletransformers` library.
```bsh
pip install simpletransformers
```

### Example Usage
```py
import pickle

model = pickle.load(open("title-generator-t5-arxiv-16-4.pkl", "rb"))

# Prefix your text with 'summarize: '
text = ["summarize: " + """Venetian commodes imitated the curving lines and carved ornament of the French rocaille, but with a particular Venetian variation; the pieces were painted, often with landscapes or flowers or scenes from Guardi or other painters, or Chinoiserie, against a blue or green background, matching the colours of the Venetian school of painters whose work decorated the salons. 24] Ceiling of church of Santi Giovanni e Paolo in Venice, by Piazzetta (1727) Juno and Luna by Giovanni Battista Tiepolo (1735–45) Murano glass chandelier at the Ca Rezzonico (1758) Ballroom ceiling of the Ca Rezzonico with ceiling by Giovanni Battista Crosato (1753) In church construction, especially in the southern German-Austrian region, gigantic spatial creations are sometimes created for practical reasons alone, which, however, do not appear monumental, but are characterized by a unique fusion of architecture, painting, stucco, etc. ,."""]

print("Generated title: " + model.predict(text))
```