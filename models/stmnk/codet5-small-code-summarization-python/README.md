---
language: 
  - py
  - en
thumbnail: "url to a thumbnail used in social sharing"
tags:
  - Code2TextGeneration
  - Code2TextSummarisation
license: apache-2.0
datasets:
  - code_x_glue_ct_code_to_text 
  - code_x_glue_ct_code_to_text (python)
metrics:
  - code-x-bleu
---

pretrained model: https://huggingface.co/Salesforce/codet5-small

finetuning dataset: https://huggingface.co/datasets/code_x_glue_ct_code_to_text (only the python split)

official inference check point (for comparison, using base, not small, size): https://storage.googleapis.com/sfr-codet5-data-research/finetuned_models/summarize_python_codet5_base.bin

for fine-tuning process metrics see [this w&b report](https://wandb.ai/stmnk/CodeT5/reports/Code-T5-code_x_glue_code2text--VmlldzoxMjM4MTUy?accessToken=5stsbg6bn2x0m6svrosxtq0zv3vhlgzr4cjcyapw52xq5puc09wo6f8li40ln7fm) 



<!-- <iframe src="https://wandb.ai/stmnk/CodeT5/reports/Code-T5-code_x_glue_code2text--VmlldzoxMjM4MTUy" style="border:none;height:1024px;width:100%"> -->

