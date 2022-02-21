# Pre-trained Conformer-CTC models for the librispeech dataset with icefall.
The model was trained on full [LibriSpeech](http://openslr.org/12/) with the scripts in [icefall](https://github.com/k2-fsa/icefall).  
See (https://github.com/k2-fsa/icefall/pull/13) for more details of this model.

## How to use
See (https://github.com/k2-fsa/icefall/blob/master/egs/librispeech/ASR/conformer_ctc/README.md)

## Training procedure
The version of the mainly repositories are list below.  
k2: https://github.com/k2-fsa/k2/commit/81cec9ec736d2c603ad75d933bb3e3a3706fb0dd  
icefall: https://github.com/k2-fsa/icefall/commit/ef233486ae6d21bacb940de45efb35d0c334605c  
lhotse: https://github.com/lhotse-speech/lhotse/commit/5dfe0f4c02b1334ebb7db6d67e1141fe406ca76b  

* Install k2 and lhotse, k2 installation guide refers to https://k2.readthedocs.io/en/latest/installation/index.html, lhotse refers to https://lhotse.readthedocs.io/en/latest/getting-started.html#installation. It is better to use the given version above, but I think the latest version would be ok. And also install the requirements listed in icefall.

* Clone icefall(https://github.com/k2-fsa/icefall) and check to the commit showed above.
```
git clone https://github.com/k2-fsa/icefall
cd icefall
git checkout ef233486
```
* Preparing data.
```
cd egs/librispeech/ASR
bash ./prepare.sh
```
* Training
```bash
export CUDA_VISIBLE_DEVICES="0,1,2,3"
python conformer_ctc/train.py --bucketing-sampler True \                                
                                --concatenate-cuts False \
                                --max-duration 200 \
                                --full-libri True \
                                --world-size 4
```

## Evaluation results
The best decoding results (WERs) on LibriSpeech test-clean and test-other are listed below, we got this results by averaging models from epoch 15 to 34.

||test-clean|test-other|
|--|--|--|
|WER|2.57%|5.94%|
