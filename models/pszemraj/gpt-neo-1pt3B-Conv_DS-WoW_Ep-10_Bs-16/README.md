# GPT-Neo for Conversation - Test 1.3B Model - 10 epochs

- idea: take GPT-Neo, fine-tune it on dialogue data, creating a chatbot that can handle off-the-hook questions.
- This model was fine-tuned on the Parl.ai **Wizard of Wikipedia** dataset _for 10 Epochs_
- note that the generations take place in a special form, with the "speaker" being `person alpha` and the "responder " being `person beta.
  - more details are in the repo [here](https://github.com/pszemraj/ai-msgbot)
  
  ```
'person alpha:\n'
 'hi! how are you doing?\n'
 '\n'
 'person beta:\n'
 "i'm doing well. i like to watch football! do you like football?\n"
 '\n'
 ```
 