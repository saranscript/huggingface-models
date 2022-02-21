## Dataset:
A variant of the Persona-Chat dataset was used, which contains 19319 short dialogues. MarianMT, a free and efficient Neural Machine Translation framework, was used to translate this dataset into Greek. 


## Fine-tuning for the task of dialogue: 
Using the pre-trained "gpt2-greek" (https://huggingface.co/nikokons/gpt2-greek) model, we fine-tune it on this Greek version of translated Persona-Chat dataset for 3 epochs until there is no progress in validation loss. The model's input is customized to the Greek version of the PERSONA-CHAT dataset to perform the fine-tuning procedure. A batch size of 4 is used, and gradients are accumulated over 8 iterations, resulting in a total batch size of 32. The Adam optimization scheme is used, with a learning rate of 5.7e-5. The fine-tuning procedure is based on the https://github.com/huggingface/transfer-learning-conv-ai repository.

## Interact with the Chatbot: 
You can interact with the chatbot in Greek using the code in this repository: https://github.com/Nkonstan/chatbot 
