## TextAttack Model Card
This `albert-base-v2` model was fine-tuned for sequence classification using TextAttack 
and the glue dataset loaded using the `nlp` library. The model was fine-tuned 
for 5 epochs with a batch size of 32, a learning 
rate of 3e-05, and a maximum sequence length of 128. 
Since this was a regression task, the model was trained with a mean squared error loss function. 
The best score the model achieved on this task was 0.9064220351504577, as measured by the 
eval set pearson correlation, found after 3 epochs.

For more information, check out [TextAttack on Github](https://github.com/QData/TextAttack).
