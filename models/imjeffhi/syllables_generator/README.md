# Syllabizer Card

A fine-tuned version of GPT-neo (small, 125M parameters) on a syllables dataset collected via web scraping. 

The model has two additional special tokens:

1. \<SPELLED\>: Is followed by the word you wish to syllabize spelled out (used to work around some aspects of tokenization). 
2. \<SYLLABLES\>: Is where the model outputs syllables in a spaced format

A sample code can be seen here:

```python
word = "syllabizer"
characters = " ".join(word)
input_string = f"{word} <SPELLED> {characters} <SYLLABLES>"
```

Output:

```python
syllabizer <SPELLED> s y l l a b i z e r <SYLLABLES> syl lab iz er <|endoftext|>
```