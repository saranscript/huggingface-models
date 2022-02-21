Toy Wordlevel Tokenizer created for testing.

Code used for its creation:

```
from tokenizers import Tokenizer, normalizers, pre_tokenizers
from tokenizers.models import WordLevel
from tokenizers.normalizers import NFD, Lowercase, StripAccents
from tokenizers.pre_tokenizers import Digits, Whitespace
from tokenizers.processors import TemplateProcessing
from tokenizers.trainers import WordLevelTrainer


SMALL_TRAINING_CORPUS = [
    ["This is the first sentence.", "This is the second one."],
    ["This sentence (contains #) over symbols and numbers 12 3.", "But not this one."],
]

tokenizer = Tokenizer(WordLevel(unk_token="[UNK]"))
tokenizer.normalizer = normalizers.Sequence([NFD(), Lowercase(), StripAccents()])

tokenizer.pre_tokenizer = pre_tokenizers.Sequence([Whitespace(), Digits(individual_digits=True)])

tokenizer.post_processor = TemplateProcessing(
    single="[CLS] $A [SEP]",
    pair="[CLS] $A [SEP] $B:1 [SEP]:1",
    special_tokens=[
        ("[CLS]", 1),
        ("[SEP]", 2),
    ],
)

trainer = WordLevelTrainer(vocab_size=100, special_tokens=["[UNK]", "[CLS]", "[SEP]", "[PAD]", "[MASK]"])

tokenizer.train_from_iterator(SMALL_TRAINING_CORPUS, trainer=trainer)

tokenizer.save("tokenizer.json")
```

```
from transformers import PreTrainedTokenizerFast

tokenizer = PreTrainedTokenizerFast(
    tokenizer_file="tokenizer.json",
    bos_token="[CLS]",
    eos_token="[SEP]",
    unk_token="[UNK]",
    sep_token="[SEP]",
    pad_token="[PAD]",
    cls_token= "[CLS]",
    mask_token="[MASK]",
    model_max_length=10,
    padding_side="right"

)

tokenizer.push_to_hub('dummy-tokenizer-wordlevel', commit_message="add tokenizer")
```