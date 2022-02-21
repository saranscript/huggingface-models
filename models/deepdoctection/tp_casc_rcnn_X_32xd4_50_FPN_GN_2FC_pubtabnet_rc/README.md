---
tags:
- Tensorflow
license: apache-2.0
datasets:
- Pubtabnet
---


# Tensorpacks Cascade-RCNN with FPN and Group Normalization on ResNext32xd4-50 trained on Pubtabnet for Semantic Segmentation of tables. 

The model and its training code has been mainly taken from: [Tensorpack](https://github.com/tensorpack/tensorpack/tree/master/examples/FasterRCNN) . 

Regarding the dataset, please check: [Xu Zhong et. all. - Image-based table recognition: data, model, and evaluation](https://arxiv.org/abs/1911.10683). 

The model has been trained on detecting rows and columns for tables. As rows and column bounding boxes are not a priori an element of the annotations they are
calculated using the bounding boxes of the cells and the intrinsic structure of the enclosed HTML.

The code has been adapted so that it can be used in a **deep**doctection pipeline. 

## How this model can be used

This model can be used with the **deep**doctection in a full pipeline, along with table recognition and OCR. Check the general instruction following this [Get_started](https://github.com/deepdoctection/deepdoctection/blob/master/notebooks/Get_Started.ipynb) tutorial.

## How this model was trained. 

To recreate the model run on the **deep**doctection framework, run:

```python
>>> import os
>>> from deep_doctection.datasets import DatasetRegistry
>>> from deep_doctection.eval import MetricRegistry
>>> from deep_doctection.utils import get_configs_dir_path
>>> from deep_doctection.train import train_faster_rcnn

pubtabnet = DatasetRegistry.get_dataset("pubtabnet")
pubtabnet.dataflow.categories.set_cat_to_sub_cat({"ITEM":"row_col"})
pubtabnet.dataflow.categories.filter_categories(categories=["ROW","COLUMN"])

path_config_yaml=os.path.join(get_configs_dir_path(),"tp/rows/conf_frcnn_rows.yaml")
path_weights = ""
dataset_train = pubtabnet

config_overwrite=["TRAIN.STEPS_PER_EPOCH=500","TRAIN.STARTING_EPOCH=1", "TRAIN.CHECKPOINT_PERIOD=50"]
build_train_config=["max_datapoints=500000","rows_and_cols=True"]
dataset_val = pubtabnet
build_val_config = ["max_datapoints=2000","rows_and_cols=True"]

coco_metric = MetricRegistry.get_metric("coco")
coco_metric.set_params(max_detections=[50,200,600], area_range=[[0,1000000],[0,200],[200,800],[800,1000000]])

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

## How to fine-tune this model

To fine tune this model, please check this [Fine-tune](https://github.com/deepdoctection/deepdoctection/blob/master/notebooks/Fine_Tune.ipynb) tutorial.