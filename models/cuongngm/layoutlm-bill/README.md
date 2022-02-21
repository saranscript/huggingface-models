Fine tuning LayoutLMv2 model on Vietnamese bill dataset 
```python
from transformers import LayoutLMv2ForTokenClassification
model = LayoutLMv2ForTokenClassification.from_pretrained('cuongngm/layoutlm-bill', num_labels=len(labels))
```