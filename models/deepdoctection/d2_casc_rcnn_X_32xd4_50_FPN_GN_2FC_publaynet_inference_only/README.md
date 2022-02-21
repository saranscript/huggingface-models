---
tags:
- Pytorch
license: apache-2.0
datasets:
- Publaynet
---


# Detectron2 Cascade-RCNN with FPN and Group Normalization on ResNext32xd4-50 trained on Publaynet for Document Layout Analysis

The model and has been trained with the Tensorflow training toolkit Tensorpack and then transferred to Pytorch using a conversion script. 
The Tensorflow and Pytorch models differ slightly (padding ...), however validating both models give a difference of less than 0.03 mAP.   

Please check: [Xu Zhong et. all. - PubLayNet: largest dataset ever for document layout analysis](https://arxiv.org/abs/1908.07836). 

This model is different from the model used the paper. 

The code has been adapted so that it can be used in a **deep**doctection pipeline. 

## How this model can be used

This model can be used with the **deep**doctection in a full pipeline, along with table recognition and OCR. Check the general instruction following this [Get_started](https://github.com/deepdoctection/deepdoctection/blob/master/notebooks/Get_Started.ipynb) tutorial.

  
## This is an inference model only

To reduce the size of the checkpoint we removed all variables that are not necessary for inference. Therefore it cannot be used for fine-tuning. To fine tune this model please use Tensorflow, as well as its training script. More information can be found in this [this model card](https://huggingface.co/deepdoctection/tp_casc_rcnn_X_32xd4_50_FPN_GN_2FC_publaynet). 

