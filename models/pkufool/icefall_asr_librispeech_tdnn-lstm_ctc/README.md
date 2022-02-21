# Pre-trained TDNN-LSTM-CTC models for the librispeech dataset with icefall.
The model was trained on full [LibriSpeech](http://openslr.org/12/) with the scripts in [icefall](https://github.com/k2-fsa/icefall).  
See (https://github.com/k2-fsa/icefall/tree/master/egs/librispeech/ASR/tdnn_lstm_ctc) for more details of this model.

## How to use
See (https://github.com/k2-fsa/icefall/blob/master/egs/librispeech/ASR/tdnn_lstm_ctc/Pre-trained.md)

## Training procedure
The version of the mainly repositories are list below.  
k2: https://github.com/k2-fsa/k2/commit/81cec9ec736d2c603ad75d933bb3e3a3706fb0dd  
icefall: https://github.com/k2-fsa/icefall/commit/7a647a13780cf011f9cfe3067e87a6ebb3bb8411  
lhotse: https://github.com/lhotse-speech/lhotse/commit/5dfe0f4c02b1334ebb7db6d67e1141fe406ca76b  

* Install k2 and lhotse, k2 installation guide refers to https://k2.readthedocs.io/en/latest/installation/index.html, lhotse refers to https://lhotse.readthedocs.io/en/latest/getting-started.html#installation. It is better to use the given version above, but I think the latest version would be ok. And also install the requirements listed in icefall.

* Clone icefall(https://github.com/k2-fsa/icefall) and check to the commit showed above.
```
git clone https://github.com/k2-fsa/icefall
cd icefall
git checkout 7a647a13780cf011f9cfe3067e87a6ebb3bb8411
```
* Preparing data.
```
cd egs/librispeech/ASR
bash ./prepare.sh
```
* Training
```
export CUDA_VISIBLE_DEVICES="0,1,2,3"
python tdnn_lstm_ctc/train.py --bucketing-sampler True \
                                --concatenate-cuts False \
                                --max-duration 200 \
                                --full-libri True \
                                --world-size 4
```

## Evaluation results
The best decoding results (WERs) on LibriSpeech test-clean and test-other are listed below, we got this results by averaging models from epoch 14 to 19, the decoding method is `whole-lattice-rescoring`.

||test-clean|test-other|
|--|--|--|
|WER|6.59%|17.69%|
