
## Pre-trained TDNN models for the yesno dataset with icefall.

Refer to <https://github.com/k2-fsa/icefall/tree/master/egs/yesno/ASR>
for more information about this pre-trained model.

You can find usage instructions there.


## Sound files for testing the pre-trained model

The folder `test_waves` contains test sound files. They
are downloaded from <https://www.openslr.org/1/>.

There are 60 files in the dataset, 30 are used for training.
The remaining 30 files, contained in `test_waves` are kept for testing.

The code for splitting the dataset can be found at
<https://github.com/lhotse-speech/lhotse/blob/master/lhotse/recipes/yesno.py#L138>

```python
wave_files = list(corpus_dir.glob("*.wav"))
assert len(wave_files) == 60

wave_files.sort()
train_set = wave_files[::2]
test_set = wave_files[1::2]

assert len(train_set) == 30
assert len(test_set) == 30
```
