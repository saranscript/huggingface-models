---
language: 
  - en
license: apache-2.0
tags:
  - hyperion
  - audio
  - speech 
  - speaker-recognition
  - x-vector
  - thin-resnet34
datasets:
 - voxceleb 
metrics:
 - eer
 - min_dcf-p=0.05
 - min_dcf-p=0.01
model-index:
 - name: voxceleb-v1.1-fbank80_stmn_lresnet34_e256_arcs30m0.3_do0_adam_lr0.05_b512.v1
   results:
   - task:
       type: speaker-verification
       name: Speaker Verification
     dataset:
       type: voxceleb1
       name: Voxceleb1
       args: Train on VoxCeleb2-dev
     metrics:
     - type: eer
       value: 2.11
       name: EER Vox1-O
     - type: min_dcf-p=0.05
       value: 0.135
       name: Minimum DCF Vox1-O prior=0.05
     - type: act_dcf-p=0.01
       value: 0.208
       name: Minimum DCF Vox1-O prior=0.01
     - type: eer
       value: 1.93
       name: EER Vox1-E
     - type: min_dcf-p=0.05
       value: 0.121
       name: Minimum DCF Vox1-E prior=0.05
     - type: act_dcf-p=0.01
       value: 0.204
       name: Minimum DCF Vox1-E Original prior=0.01
     - type: eer
       value: 3.21
       name: EER Vox1-H
     - type: min_dcf-p=0.05
       value: 0.190
       name: Minimum DCF Vox1-H prior=0.05
     - type: act_dcf-p=0.01
       value: 0.298
       name: Minimum DCF Vox1-H Original prior=0.01
---
# Hyperion Toolkit Speaker Verification pre-trained Model

## Model Configuration
This model was trained using recipe [voxceleb/v1.1](https://github.com/hyperion-ml/hyperion/tree/master/egs/voxceleb/v1.1)

The configuration for this modeis is defined in
[config_fbank80_stmn_lresnet34_arcs30m0.3_adam_lr0.05_amp.v1.sh](https://github.com/hyperion-ml/hyperion/blob/master/egs/voxceleb/v1.1/global_conf/config_fbank80_stmn_lresnet34_arcs30m0.3_adam_lr0.05_amp.v1.sh)

This is an x-vector model with:
  - 80 logMel filter-banks with short-time mean normalization.
  - ThinResNet34 (aka Light ResNet34) encoder.
  - Mean+Stddev pooling
  - AAM-softmax loss (m=0.3, s=30)
  - Mixed prec. training.
