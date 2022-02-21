from transformers import RobertaTokenizerFast
tokenizer = RobertaTokenizerFast.from_pretrained('Andrija/RobertaFastBPE', bos_token="&lt;s&gt;", eos_token="&lt;/s&gt;")

encoded = tokenizer('Stručnjaci te bolnice, predvođeni dr Alisom Lim')
# {'input_ids': [0, 47541, 34632, 603, 24817, 16, 27540, 6768, 2350, 2803, 3991, 2733, 81, 1], 'attention_mask': [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]}
tokenizer.decode(encoded['input_ids'])
# &lt;s&gt;Stručnjaci te bolnice, predvođeni dr Alisom Lim&lt;/s&gt;