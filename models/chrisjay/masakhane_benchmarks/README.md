---
language: african-languages
tags:
- african-languages
- machine-translation
- text
license: apache-2.0
model-index:
- name: Masakhane Benchmark Models
  results:
  - task: 
      name: Machine Translation
      type: machine-translation
    dataset:
      name: masakhane benchmarks
      args: african-languages
   
---
# Interacting with the Masakhane Benchmark Models

I created this demo for very easy interaction with the [benchmark models on Masakhane](https://github.com/masakhane-io/masakhane-mt/tree/master/benchmarks) which were trained with [JoeyNMT](https://github.com/chrisemezue/joeynmt)(my forked version).

To access the space click [here](https://huggingface.co/spaces/chrisjay/masakhane-benchmarks).

To include your language, all you need to do is:
1. Create a folder in the format *src-tgt/main* for your language pair, if it does not exist.
2. Inside the *main* folder put the following files:
    1. model checkpoint. Rename it to `best.ckpt`.
    2. `config.yaml` file. This is the JoeyNMT config file which loads the model an pre-processing parameters.
    3. `src_vocab.txt` file.
    4. `trg_vocab.txt` file.
    
The space currently supports these languages:

| source language | target language |
|:---------------:|:---------------:|
| English         | Swahili         |
| English         | Afrikaans       |
| English         | Arabic          |
| English         | Urhobo          |
| English         | Ẹ̀dó             |
| Efik            | English         |
| English         | Hausa           |
| English         | Igbo            |
| English         | Fon             |
| English         | Twi             |
| English         | Dendi           |
| English         | Ẹ̀sán             |
| English         | Isoko           |
| English         | Kamba           |
| English         | Luo           |
| English         | Southern Ndebele  |
| English         | Tshivenda           |
| Shona           | English         |
| Swahili         | English         |
| Yoruba          | English         |

TO DO:
1. Include more languages from the benchmark.