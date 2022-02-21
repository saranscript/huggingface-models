---
tags:
- Tensorflow
license: apache-2.0
datasets:
- Publaynet
---


# Tensorpacks Cascade-RCNN with FPN and Group Normalization on ResNext32xd4-50 trained on Publaynet for Document Layout Analysis

The model and its training code has been mainly taken from: [Tensorpack](https://github.com/tensorpack/tensorpack/tree/master/examples/FasterRCNN) . 

Please check: [Xu Zhong et. all. - PubLayNet: largest dataset ever for document layout analysis](https://arxiv.org/abs/1908.07836). 

This model is different from the model used the paper. 

The code has been adapted so that it can be used in a **deep**doctection pipeline. 

## How this model can be used

This model can be used with the **deep**doctection in a full pipeline, along with table recognition and OCR. Check the general instruction following this [Get_started](https://github.com/deepdoctection/deepdoctection/blob/master/notebooks/Get_Started.ipynb) tutorial.

  
## This is an inference model only

To reduce the size of the checkpoint we removed all variables that are not necessary for inference. Therefore it cannot be used for fine-tuning. To fine tune this model please check [this model](https://huggingface.co/deepdoctection/tp_casc_rcnn_X_32xd4_50_FPN_GN_2FC_publaynet).


## How this model was trained. 

To recreate the model run on the **deep**doctection framework, run:

```python
>>> import os
>>> from deep_doctection.datasets import DatasetRegistry
>>> from deep_doctection.eval import MetricRegistry
>>> from deep_doctection.utils import get_configs_dir_path
>>> from deep_doctection.train import train_faster_rcnn

publaynet = DatasetRegistry.get_dataset("publaynet")
path_config_yaml=os.path.join(get_configs_dir_path(),"tp/layout/conf_frcnn_layout.yaml")
path_weights = ""
dataset_train = publaynet
config_overwrite=["TRAIN.STEPS_PER_EPOCH=500","TRAIN.EVAL_PERIOD=200","TRAIN.STARTING_EPOCH=1",
                  "PREPROC.TRAIN_SHORT_EDGE_SIZE=[800,1200]","TRAIN.CHECKPOINT_PERIOD=50",
                  "BACKBONE.FREEZE_AT=0"]
build_train_config=["max_datapoints=335703"]
dataset_val = publaynet
build_val_config = ["max_datapoints=2000"]
    
coco_metric = MetricRegistry.get_metric("coco")

train_faster_rcnn(path_config_yaml=path_config_yaml,
                  dataset_train=dataset_train,
                  path_weights=path_weights,
                  config_overwrite=config_overwrite,
                  log_dir="/path/to/dir",
                  build_train_config=build_train_config,
                  dataset_val=dataset_val,
                  build_val_config=build_val_config,
                  metric=coco_metric,
                  pipeline_component_name="ImageLayoutService"
                  )
```