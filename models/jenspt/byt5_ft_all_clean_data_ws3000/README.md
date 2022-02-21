training_args = TrainingArguments(
    output_dir='./results',          # output directory
    num_train_epochs=1,              # total number of training epochs
    per_device_train_batch_size=8,  # batch size per device during training
    #per_device_eval_batch_size=2,   # batch size for evaluation
    warmup_steps=3000,                # number of warmup steps for learning rate scheduler (used to be 500)
    weight_decay=0.01,               # strength of weight decay
    #learning_rate=0.1e-3, # default = 5e-5=0.5e-4
    logging_dir='./logs',            # directory for storing logs
    logging_steps=50,
    #eval_steps = 100,
    overwrite_output_dir = True,
    save_strategy = 'epoch',
    #logging_strategy = 'epoch',
)