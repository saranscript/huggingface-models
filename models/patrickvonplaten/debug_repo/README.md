This repository is used to debug models, functionalities in transformers, etc...

# 1. Generation

...

# 2. Flax Wav2Vec2 Pretraining

Go into the `flax_wav2vec2` folder.

1. **Check PT loss works correctly**

`./run_pt_fsq_comp.sh` shows that HF PyTorch and Fairseq PT yield equivalent loss. Make sure to use the correct library versions as defined `branches_to_use.txt`.

2. **Check Flax loss works correctly**

`./run_flax_fsq_comp.sh` shows that HF PyTorch and HF Flax yield equivalent loss. Make sure to use the correct library versions as defined `branches_to_use.txt`.