I've converted the DINO checkpoints from the [official repo](https://github.com/facebookresearch/dino): 

You can use it as follows:

```python
from transformers import ViTModel

model = ViTModel.from_pretrained("nielsr/dino_vitb16", add_pooling_layer=False)

```