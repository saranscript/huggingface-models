# GPT2 Fine Tuned on UrbanDictionary
Honestly a little horrifying, but still funny.

## Usage
Use with GPT2Tokenizer. Pad token should be set to the EOS token.
Inputs should be of the form "define <your word>: ".

## Training Data
All training data was obtained from [Urban Dictionary Words And Definitions on Kaggle](https://www.kaggle.com/therohk/urban-dictionary-words-dataset). Data was additionally filtered, normalized, and spell-checked.

## Bias
This model was trained on public internet data and will almost definitely produce offensive results. Some efforts were made to reduce this (i.e definitions with ethnic / gender-based slurs were removed), but the final model should not be trusted to produce non-offensive definitions.