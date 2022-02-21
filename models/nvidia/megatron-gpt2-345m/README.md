<!---
# ##############################################################################################
# 
# Copyright (c) 2021-, NVIDIA CORPORATION.  All rights reserved.
# 
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
# 
#     http://www.apache.org/licenses/LICENSE-2.0
# 
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# 
# ##############################################################################################
-->

[Megatron](https://arxiv.org/pdf/1909.08053.pdf) is a large, powerful transformer developed by the Applied Deep Learning Research team at NVIDIA. This particular Megatron model was trained from a generative, left-to-right transformer in the style of GPT-2. This model was trained on text sourced from Wikipedia, RealNews, OpenWebText, and CC-Stories. It contains 345 million parameters. 

Find more information at [https://github.com/NVIDIA/Megatron-LM](https://github.com/NVIDIA/Megatron-LM)

# How to run Megatron GPT2 using Transformers

## Prerequisites 

In that guide, we run all the commands from a folder called `$MYDIR` and defined as (in `bash`):

```
export MYDIR=$HOME
```

Feel free to change the location at your convenience.

To run some of the commands below, you'll have to clone `Transformers`. 

```
git clone https://github.com/huggingface/transformers.git $MYDIR/transformers
```

## Get the checkpoints from the NVIDIA GPU Cloud 

You must create a directory called `nvidia/megatron-gpt2-345m`:

```
mkdir -p $MYDIR/nvidia/megatron-gpt2-345m
```

You can download the checkpoints from the [NVIDIA GPU Cloud (NGC)](https://ngc.nvidia.com/catalog/models/nvidia:megatron_lm_345m). For that you
have to [sign up](https://ngc.nvidia.com/signup) for and setup the NVIDIA GPU
Cloud (NGC) Registry CLI.  Further documentation for downloading models can be
found in the [NGC
documentation](https://docs.nvidia.com/dgx/ngc-registry-cli-user-guide/index.html#topic_6_4_1).

Alternatively, you can directly download the checkpoints using:

```
wget --content-disposition https://api.ngc.nvidia.com/v2/models/nvidia/megatron_lm_345m/versions/v0.0/zip -O $MYDIR/nvidia/megatron-gpt2-345m/checkpoint.zip
```

## Converting the checkpoint

In order to be loaded into `Transformers`, the checkpoint has to be converted. You should run the following command for that purpose. 
That command will create `config.json` and `pytorch_model.bin` in `$MYDIR/nvidia/megatron-gpt2-345m`. 
You can move those files to different directories if needed.

```
python3 $MYDIR/transformers/src/transformers/models/megatron_gpt2/convert_megatron_gpt2_checkpoint.py $MYDIR/nvidia/megatron-gpt2-345m/checkpoint.zip
```

As explained in [PR #14956](https://github.com/huggingface/transformers/pull/14956), if when running this conversion 
script and you're getting an exception:
```
ModuleNotFoundError: No module named 'megatron.model.enums'
```
you need to tell python where to find the clone of Megatron-LM, e.g.:
```
cd /tmp
git clone https://github.com/NVIDIA/Megatron-LM
PYTHONPATH=/tmp/Megatron-LM python src/transformers/models/megatron_bert/convert_megatron_bert_checkpoint.py ...
```
Or, if you already have it cloned elsewhere, simply adjust the path to the existing path.

If the training was done using a Megatron-LM fork, e.g. [Megatron-DeepSpeed](https://github.com/microsoft/Megatron-DeepSpeed/) then 
you may need to have that one in your path, i.e., /path/to/Megatron-DeepSpeed.

## Text generation

The following code shows how to use the Megatron GPT2 checkpoint and the Transformers API to generate text.

```
import os
import torch

from transformers import GPT2Tokenizer, GPT2LMHeadModel

# The tokenizer. Megatron was trained with standard tokenizer(s).
tokenizer = GPT2Tokenizer.from_pretrained('gpt2')
# The path to the config/checkpoint (see the conversion step above).
directory = os.path.join(os.environ['MYDIR'], 'nvidia/megatron-gpt2-345m')
# Load the model from $MYDIR/nvidia/megatron-gpt2-345m.
model = GPT2LMHeadModel.from_pretrained(directory)

# Copy to the device and use FP16.
assert torch.cuda.is_available()
device = torch.device("cuda")
model.to(device)
model.eval()
model.half()

# Generate the sentence.
output = model.generate(input_ids=None, max_length=32, num_return_sequences=1)

# Output the text.
for sentence in output:
    sentence = sentence.tolist()
    text = tokenizer.decode(sentence, clean_up_tokenization_spaces=True)
    print(text)
```

# To use this as a normal HuggingFace model

If you want to use this model with HF Trainer, here is a quick way to do that:

1. Download nvidia checkpoint:
```
wget --content-disposition https://api.ngc.nvidia.com/v2/models/nvidia/megatron_lm_345m/versions/v0.0/zip -O megatron_lm_345m_v0.0.zip
```

2. Convert:
```
python src/transformers/models/megatron_gpt2/convert_megatron_gpt2_checkpoint.py megatron_lm_345m_v0.0.zip
```

3. Fetch missing files
```
git clone https://huggingface.co/nvidia/megatron-gpt2-345m/
```

4. Move the converted files into the cloned model dir
```
mv config.json pytorch_model.bin megatron-gpt2-345m/
```

5. The `megatron-gpt2-345m` dir should now have all the files which can be passed to HF Trainer as  `--model_name_or_path megatron-gpt2-345m`


# Original code

The original Megatron code can be found here: [https://github.com/NVIDIA/Megatron-LM](https://github.com/NVIDIA/Megatron-LM).
