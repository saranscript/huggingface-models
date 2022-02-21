CLIP model retrained over some subset of the DPC dataset

### Usage instructions

```
from transformers import AutoTokenizer, AutoModel, CLIPProcessor

tokenizer = AutoTokenizer.from_pretrained("vicgalle/clip-vit-base-patch16-photo-critique")
model = AutoModel.from_pretrained("vicgalle/clip-vit-base-patch16-photo-critique", from_flax=True)
processor = CLIPProcessor.from_pretrained("vicgalle/clip-vit-base-patch16-photo-critique")
```
