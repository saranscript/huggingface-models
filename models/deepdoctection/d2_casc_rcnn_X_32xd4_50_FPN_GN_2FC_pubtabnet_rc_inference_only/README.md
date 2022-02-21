---
tags:
- Pytorch
license: apache-2.0
datasets:
- Pubtabnet
---


# Detectron2 Cascade-RCNN with FPN and Group Normalization on ResNext32xd4-50 trained on Pubtabnet for Semantic Segmentation of tables. 

The model and has been trained with the Tensorflow training toolkit Tensorpack and then transferred to Pytorch using a conversion script. 
The Tensorflow and Pytorch models differ slightly (padding ...), however validating both models give a difference of less than 0.03 mAP.   

Regarding the dataset, please check: [Xu Zhong et. all. - Image-based table recognition: data, model, and evaluation](https://arxiv.org/abs/1911.10683). 

The model has been trained on detecting rows and columns for tables. As rows and column bounding boxes are not a priori an element of the annotations they are
calculated using the bounding boxes of the cells and the intrinsic structure of the enclosed HTML.

The code has been adapted so that it can be used in a **deep**doctection pipeline. 

## How this model can be used

This model can be used with the **deep**doctection in a full pipeline, along with table recognition and OCR. Check the general instruction following this [Get_started](https://github.com/deepdoctection/deepdoctection/blob/master/notebooks/Get_Started.ipynb) tutorial.

  
## This is an inference model only

To reduce the size of the checkpoint we removed all variables that are not necessary for inference. Therefore it cannot be used for fine-tuning. To fine tune this model please use Tensorflow, as well as its training script. More information can be found in this [this model card](https://huggingface.co/deepdoctection/tp_casc_rcnn_X_32xd4_50_FPN_GN_2FC_pubtabnet_rc). 