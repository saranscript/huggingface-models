# Pre-trained VisualNet2-CTC models for the GRID visual dataset with icefall.
The model was trained on full [GRID](https://zenodo.org/record/3625687#.Ybn7HagzY2w) with the scripts in [icefall](https://github.com/k2-fsa/icefall).  
See (https://github.com/k2-fsa/icefall/tree/master/egs/grid/AVSR/visualnet2_ctc_asr) for more details of this model.
## How to use
See (https://github.com/k2-fsa/icefall/blob/master/egs/grid/AVSR/visualnet2_ctc_asr/Pre-trained.md)
## Training procedure
The main repositories are list below, we will update the training and decoding scripts with the update of version.  
k2: https://github.com/k2-fsa/k2 
icefall: https://github.com/k2-fsa/icefall 
* Install k2 and lhotse, k2 installation guide refers to https://k2.readthedocs.io/en/latest/installation/index.html, lhotse refers to https://lhotse.readthedocs.io/en/latest/getting-started.html#installation. I think the latest version would be ok. And please also install the requirements listed in icefall.
* Clone icefall(https://github.com/k2-fsa/icefall) and check to the commit showed above.
```
git clone https://github.com/k2-fsa/icefall
cd icefall
```
* Preparing data.
```
cd egs/grid/AVSR
bash ./prepare.sh
```
* Training
```
export CUDA_VISIBLE_DEVICES="0"
python visualnet2_ctc_asr/train.py --world-size 1
```
## Evaluation results
The best decoding results (WER) on GRID TEST are listed below, we got this result by averaging models from epoch 15 to 29, the decoding method is `1best`.
||TEST|
|--|--|
|WER|13.63%|