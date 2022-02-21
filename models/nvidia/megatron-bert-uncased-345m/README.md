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

[Megatron](https://arxiv.org/pdf/1909.08053.pdf) is a large, powerful transformer developed by the Applied Deep Learning Research team at NVIDIA. This particular Megatron model was trained from a bidirectional transformer in the style of BERT with text sourced from Wikipedia, RealNews, OpenWebText, and CC-Stories. This model contains 345 million parameters. It is made up of 24 layers, 16 attention heads with a hidden size of 1024. 

Find more information at [https://github.com/NVIDIA/Megatron-LM](https://github.com/NVIDIA/Megatron-LM)


# How to run Megatron BERT using Transformers

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

## Get the checkpoint from the NVIDIA GPU Cloud 

You must create a directory called `nvidia/megatron-bert-uncased-345m`.

```
mkdir -p $MYDIR/nvidia/megatron-bert-uncased-345m
```

You can download the checkpoint from the [NVIDIA GPU Cloud (NGC)](https://ngc.nvidia.com/catalog/models/nvidia:megatron_bert_345m). For that you
have to [sign up](https://ngc.nvidia.com/signup) for and setup the NVIDIA GPU
Cloud (NGC) Registry CLI.  Further documentation for downloading models can be
found in the [NGC
documentation](https://docs.nvidia.com/dgx/ngc-registry-cli-user-guide/index.html#topic_6_4_1).

Alternatively, you can directly download the checkpoint using:

```
wget --content-disposition https://api.ngc.nvidia.com/v2/models/nvidia/megatron_bert_345m/versions/v0.1_uncased/zip -O $MYDIR/nvidia/megatron-bert-uncased-345m/checkpoint.zip
```

## Converting the checkpoint

In order to be loaded into `Transformers`, the checkpoint has to be converted. You should run the following commands for that purpose. 
Those commands will create `config.json` and `pytorch_model.bin` in `$MYDIR/nvidia/megatron-bert-{cased,uncased}-345m`. 
You can move those files to different directories if needed.

```
python3 $MYDIR/transformers/src/transformers/models/megatron_bert/convert_megatron_bert_checkpoint.py $MYDIR/nvidia/megatron-bert-uncased-345m/checkpoint.zip
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

## Masked LM

The following code shows how to use the Megatron BERT checkpoint and the Transformers API to perform a `Masked LM` task.

```
import os
import torch

from transformers import BertTokenizer, MegatronBertForMaskedLM

# The tokenizer. Megatron was trained with standard tokenizer(s).
tokenizer = BertTokenizer.from_pretrained('nvidia/megatron-bert-uncased-345m')
# The path to the config/checkpoint (see the conversion step above).
directory = os.path.join(os.environ['MYDIR'], 'nvidia/megatron-bert-uncased-345m')
# Load the model from $MYDIR/nvidia/megatron-bert-uncased-345m.
model = MegatronBertForMaskedLM.from_pretrained(directory)

# Copy to the device and use FP16.
assert torch.cuda.is_available()
device = torch.device("cuda")
model.to(device)
model.eval()
model.half()

# Create inputs (from the BERT example page).
input = tokenizer("The capital of France is [MASK]", return_tensors="pt").to(device)
label = tokenizer("The capital of France is Paris",  return_tensors="pt")["input_ids"].to(device)

# Run the model.
with torch.no_grad():
    output = model(**input, labels=label)
    print(output)
```

## Next sentence prediction

The following code shows how to use the Megatron BERT checkpoint and the Transformers API to perform next
sentence prediction.

```
import os
import torch

from transformers import BertTokenizer, MegatronBertForNextSentencePrediction

# The tokenizer. Megatron was trained with standard tokenizer(s).
tokenizer = BertTokenizer.from_pretrained('nvidia/megatron-bert-uncased-345m')
# The path to the config/checkpoint (see the conversion step above).
directory = os.path.join(os.environ['MYDIR'], 'nvidia/megatron-bert-uncased-345m')
# Load the model from $MYDIR/nvidia/megatron-bert-uncased-345m.
model = MegatronBertForNextSentencePrediction.from_pretrained(directory)

# Copy to the device and use FP16.
assert torch.cuda.is_available()
device = torch.device("cuda")
model.to(device)
model.eval()
model.half()

# Create inputs (from the BERT example page).
input = tokenizer('In Italy, pizza served in formal settings is presented unsliced.',
                  'The sky is blue due to the shorter wavelength of blue light.',
                  return_tensors='pt').to(device)
label = torch.LongTensor([1]).to(device)

# Run the model.
with torch.no_grad():
    output = model(**input, labels=label)
    print(output)
```

# Original code

The original code for Megatron can be found here: [https://github.com/NVIDIA/Megatron-LM](https://github.com/NVIDIA/Megatron-LM).
