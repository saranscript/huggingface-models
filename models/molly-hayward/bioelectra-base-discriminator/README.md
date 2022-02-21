To produce BioELECTRA, we pretrain ELECTRA on a corpus of over 20 million abstracts from PubMed.

How to use the discriminator in transformers:

    from transformers import ElectraForPreTraining, ElectraTokenizerFast
    import torch
    discriminator = ElectraForPreTraining.from_pretrained("molly-hayward/bioelectra-base-discriminator")
    tokenizer = ElectraTokenizerFast.from_pretrained("molly-hayward/bioelectra-base-discriminator")