---
tags:
- image-classification
- pytorch
- medical
- colon
metrics:
- accuracy: 0.93
---

# Vision Transformer fine-tuned on kvasir_v2 for colonoscopy classification

## Demo

### Drag the following images to the widget to test the model

- ![](https://i.imgur.com/2ykziCJ_d.webp?maxwidth=224&fidelity=grand)

- ![](https://i.imgur.com/NfWPHkj_d.webp?maxwidth=224&fidelity=grand)

- ![](https://i.imgur.com/C3RexVQ_d.webp?maxwidth=224&fidelity=grand)

- ![](https://i.imgur.com/qcCYpN9_d.webp?maxwidth=224&fidelity=grand)


## Training

You can find the code [here](https://github.com/qanastek/HugsVision/blob/main/recipes/kvasir_v2/binary_classification/Kvasir_v2_Image_Classifier.ipynb)


## Metrics

```
                        precision    recall  f1-score   support

    dyed-lifted-polyps       0.95      0.93      0.94        60
dyed-resection-margins       0.97      0.95      0.96        64
           esophagitis       0.93      0.79      0.85        67
          normal-cecum       1.00      0.98      0.99        54
        normal-pylorus       0.95      1.00      0.97        57
         normal-z-line       0.82      0.93      0.87        67
                polyps       0.92      0.92      0.92        52
    ulcerative-colitis       0.93      0.95      0.94        59

              accuracy                           0.93       480
             macro avg       0.93      0.93      0.93       480
          weighted avg       0.93      0.93      0.93       480
```

## How to use

```py
from transformers import ViTFeatureExtractor, ViTForImageClassification
from hugsvision.inference.VisionClassifierInference import VisionClassifierInference

path = "mrm8488/vit-base-patch16-224_finetuned-kvasirv2-colonoscopy"


classifier = VisionClassifierInference(
    feature_extractor = ViTFeatureExtractor.from_pretrained(path),
    model = ViTForImageClassification.from_pretrained(path),
)

img  = "Your image path"
label = classifier.predict(img_path=img)
print("Predicted class:", label)
```

> Disclaimer: This model was trained for research only

> Created by [Manuel Romero/@mrm8488](https://twitter.com/mrm8488) | [LinkedIn](https://www.linkedin.com/in/manuel-romero-cs/)

> Made with <span style="color: #e25555;">&hearts;</span> in Spain