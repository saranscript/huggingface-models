---
language: sv
widget:
- text: "Jag är en svensk språkmodell."
---

## Model series
This model is part of a series of models training on TPU with Flax Jax during Huggingface Flax/Jax challenge.

## Gpt models

## Swedish Gpt
https://huggingface.co/birgermoell/swedish-gpt/

## Swedish gpt wiki
https://huggingface.co/flax-community/swe-gpt-wiki

# Nordic gpt wiki
https://huggingface.co/flax-community/nordic-gpt-wiki

## Dansk gpt wiki
https://huggingface.co/flax-community/dansk-gpt-wiki

## Norsk gpt wiki
https://huggingface.co/flax-community/norsk-gpt-wiki

## Roberta models

## Nordic Roberta Wiki
https://huggingface.co/flax-community/nordic-roberta-wiki

## Swe Roberta Wiki Oscar
https://huggingface.co/flax-community/swe-roberta-wiki-oscar

## Roberta Swedish Scandi
https://huggingface.co/birgermoell/roberta-swedish-scandi

## Roberta Swedish
https://huggingface.co/birgermoell/roberta-swedish

## Swedish T5 model
https://huggingface.co/birgermoell/t5-base-swedish



# GPT-svenska-wikipedia
A swedish GPT2 style model trained using Flax CLM pipeline on the Swedish
part of the wiki40b dataset and the Oscar dataset. 
https://huggingface.co/datasets/wiki40b

The model was trained for around 22600 steps (42 hours) as part of the Huggingface Jax/Flax challenge with the following loss and learning rate
Loss: 3.1715331077575684, Learning Rate: 0.0024816440418362617)    

The model could likely be trained for longer.

## Data cleaning and preprocessing
The data was cleaned and preprocessed using the following script. Make sure to install depencies for beam_runner to make the dataset work.

```python
from datasets import load_dataset
def load_and_clean_wiki():
    dataset = load_dataset('wiki40b', 'sv', beam_runner='DirectRunner', split="train")
    #dataset = load_dataset('wiki40b', 'sv', beam_runner='DirectRunner')
    dataset = dataset.remove_columns(['wikidata_id', 'version_id'])
    filtered_dataset = dataset.map(filter_wikipedia)
    # filtered_dataset[:3]
    # print(filtered_dataset[:3])
    return filtered_dataset

def filter_wikipedia(batch):
    batch["text"] = " ".join(batch["text"].split("\
_START_SECTION_\
"))
    batch["text"] = " ".join(batch["text"].split("\
_START_ARTICLE_\
"))
    batch["text"] = " ".join(batch["text"].split("\
_START_ARTICLE_\
"))
    batch["text"] = " ".join(batch["text"].split("\
_START_PARAGRAPH_\
"))
    batch["text"] = " ".join(batch["text"].split("_NEWLINE_"))
    batch["text"] = " ".join(batch["text"].split("\xa0"))
    return batch
```

## Training script
The following training script was used to train the model.
```bash
./run_clm_flax.py     --output_dir="${MODEL_DIR}"     --model_type="gpt2"     --config_name="${MODEL_DIR}"     --tokenizer_name="${MODEL_DIR}"     --dataset_name="wiki40b"     --dataset_config_name="sv"     --do_train --do_eval     --block_size="512"     --per_device_train_batch_size="64"     --per_device_eval_batch_size="64"     --learning_rate="5e-3" --warmup_steps="1000"     --adam_beta1="0.9" --adam_beta2="0.98" --weight_decay="0.01"     --overwrite_output_dir     --num_train_epochs="20"     --logging_steps="500"     --save_steps="1000"     --eval_steps="2500"     --push_to_hub
```

