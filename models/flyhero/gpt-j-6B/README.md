### Model Description
GPT-J 6B is a transformer model designed using EleutherAI's replication of the GPT-3 architecture. GPT-J refers to the class of models, while 6B represents the number of parameters of this particular pre-trained model.

The original GPT-J-6B model is trained with TPUs, which is not easy to use for normal users. Thus, through a converting script, we convert the TPU version GPT-J-6B into GPU version, which could be load and fine-tuned with GPUs.

As we have tried, the model can be loaded with 1 GPU with 16G memory to do inference. For fine-tune, we used 8 * 32G GPUs with DeepSpeed library to distribute the model, data and gradients, in order to allocate the huge amount of model parameters. 