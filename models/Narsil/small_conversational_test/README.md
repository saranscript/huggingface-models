```python
import tempfile                                                                   
                                                                                  
from tokenizers import Tokenizer, models, processors                              
from transformers.tokenization_utils_fast import PreTrainedTokenizerFast          
                                                                                  
vocab = [(chr(i), i) for i in range(256)]                                         
tokenizer = Tokenizer(models.Unigram(vocab))                                      
tokenizer.add_special_tokens(["<bos>", "<eos>"])                                  
tokenizer.post_processor = processors.TemplateProcessing(                         
    single="<bos> $0 <eos>", special_tokens=[("<bos>", 256), ("<eos>", 257)]      
)                                                                                 
with tempfile.NamedTemporaryFile() as f:                                          
    tokenizer.save(f.name)                                                        
    real_tokenizer = PreTrainedTokenizerFast(tokenizer_file=f.name, eos_token="<eos>", bos_token="<bos>")   
                                                                                  
real_tokenizer._tokenizer.save("dummy.json")     
``` 

Small change.
