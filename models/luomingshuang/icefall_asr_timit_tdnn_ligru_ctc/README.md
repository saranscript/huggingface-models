# Pre-trained TDNN-LiGRU-CTC models for the TIMIT dataset with icefall.
The model was trained on full [TIMIT](https://data.deepai.org/timit.zip) with the scripts in [icefall](https://github.com/k2-fsa/icefall).  
See (https://github.com/k2-fsa/icefall/tree/master/egs/timit/ASR/tdnn_ligru_ctc) for more details of this model.
## How to use
See (https://github.com/k2-fsa/icefall/blob/master/egs/timit/ASR/tdnn_ligru_ctc/Pre-trained.md)
## Training procedure
The main repositories are list below, we will update the training and decoding scripts with the update of version.  
k2: https://github.com/k2-fsa/k2 
icefall: https://github.com/k2-fsa/icefall 
lhotse: https://github.com/lhotse-speech/lhotse
* Install k2 and lhotse, k2 installation guide refers to https://k2.readthedocs.io/en/latest/installation/index.html, lhotse refers to https://lhotse.readthedocs.io/en/latest/getting-started.html#installation. I think the latest version would be ok. And please also install the requirements listed in icefall.
* Clone icefall(https://github.com/k2-fsa/icefall) and check to the commit showed above.
```
git clone https://github.com/k2-fsa/icefall
cd icefall
```
* Preparing data.
```
cd egs/timit/ASR
bash ./prepare.sh
```
* Training
```
export CUDA_VISIBLE_DEVICES="0"
python tdnn_ligru_ctc/train.py --bucketing-sampler True \
                                --concatenate-cuts False \
                                --max-duration 200 \
                                --world-size 1
```
## Evaluation results
The best decoding results (PER, equals to WER) on TIMIT TEST are listed below, we got this result by averaging models from epoch 9 to 25, the lm_scale is 0.1, the decoding method is `whole-lattice-rescoring`.
||TEST|
|--|--|
|PER|17.66%|