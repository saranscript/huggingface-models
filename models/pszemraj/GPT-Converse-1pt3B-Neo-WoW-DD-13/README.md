A text generation model that consists of the following:

1. trained GPT-Neo 1.3 B checkpoint
2. fine-tune on Parl AI [Wizard of Wikipedia](https://parl.ai/projects/wizard_of_wikipedia/) for 10 epochs  - this checkpoint is [here](https://huggingface.co/pszemraj/gpt-neo-1pt3B-Conv_DS-WoW_Ep-10_Bs-16)
3. fine-tune on the [Daily Dialogues](http://yanran.li/dailydialog) dataset for 3 epochs
