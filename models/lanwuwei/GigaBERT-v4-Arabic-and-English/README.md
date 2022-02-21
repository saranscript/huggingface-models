## GigaBERT-v4
GigaBERT-v4 is a continued pre-training of [GigaBERT-v3](https://huggingface.co/lanwuwei/GigaBERT-v3-Arabic-and-English) on code-switched data, showing improved zero-shot transfer performance from English to Arabic on information extraction (IE) tasks. More details can be found in the following paper:

	@inproceedings{lan2020gigabert,
	  author     = {Lan, Wuwei and Chen, Yang and Xu, Wei and Ritter, Alan},
  	  title      = {GigaBERT: Zero-shot Transfer Learning from English to Arabic},
  	  booktitle  = {Proceedings of The 2020 Conference on Empirical Methods on Natural Language Processing (EMNLP)},
  	  year       = {2020}
  	} 

## Download
```
from transformers import *
tokenizer = BertTokenizer.from_pretrained("lanwuwei/GigaBERT-v4-Arabic-and-English", do_lower_case=True)
model = BertForTokenClassification.from_pretrained("lanwuwei/GigaBERT-v4-Arabic-and-English")
```
Here is downloadable link [GigaBERT-v4](https://drive.google.com/drive/u/1/folders/1uFGzMuTOD7iNsmKQYp_zVuvsJwOaIdar).

