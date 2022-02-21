## TextAttack Model Card    
    This `bert-base-cased` model was fine-tuned for sequence classificationusing TextAttack 
    and the glue dataset loaded using the `nlp` library. The model was fine-tuned 
    for 3 epochs with a batch size of 128, a learning 
    rate of 1e-05, and a maximum sequence length of 128. 
    Since this was a regression task, the model was trained with a mean squared error loss function. 
    The best score the model achieved on this task was 0.8244429996636282, as measured by the 
    eval set pearson correlation, found after 2 epochs.
    
    For more information, check out [TextAttack on Github](https://github.com/QData/TextAttack).
