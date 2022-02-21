To produce BioELECTRA, we pretrain ELECTRA on a corpus of over 20 million abstracts from PubMed.

How to use the generator in transformers:

    from transformers import ElectraForMaskedLM, ElectraTokenizerFast
    import torch
    generator = ElectraForMaskedLM.from_pretrained("molly-hayward/bioelectra-base-generator")
    tokenizer = ElectraTokenizerFast.from_pretrained("molly-hayward/bioelectra-base-generator")