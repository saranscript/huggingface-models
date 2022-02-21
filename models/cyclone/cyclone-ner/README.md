## Cyclone Chinese NER

This model provides simplified Chinese NER model based on pretrained model BERT (specifically BERT + CRF)
Currently, we only support 8 general type of entities ("address", "company", "government", "name", "organization", "position", "scene", "time")

### Usage
    from transformers import BertConfig

    config = BertConfig.from_pretrained("bert-base-chinese", num_labels=num_labels)

    model_path = "cyclone/cyclone-ner"

    tokenizer = CNerTokenizer.from_pretrained(model_path, do_lower_case=True)
    model = BertCrfForNer.from_pretrained(model_path, config=config)
