# Question & Answering Model for 'Save Your Minutes' from Dobby-AI 

Electra_Large Discriminator fine-tuned on SQuAD2.0 and custom QA dataset

This model is [ahotrod/electra_large_discriminator_squad2_512](https://huggingface.co/ahotrod/electra_large_discriminator_squad2_512/blob/main/README.md)
 trained on additional custom dataset as:
 
```
!python3 run_squad.py  --model_type electra \
						--model_name_or_path /content/electra_large_512 \
						--do_lower_case \
						--output_dir /content/model/\
						--do_train \
						--train_file $data_dir/additional_qa.json\
						--version_2_with_negative \
						--do_lower_case \
						--num_train_epochs 3 \
						--weight_decay 0.01 \
						--learning_rate 3e-5 \
						--max_grad_norm 0.5 \
						--adam_epsilon 1e-6 \
						--max_seq_length 512 \
						--doc_stride 128 \
						--threads 12 \
						--logging_steps 50 \
						--save_steps 1000 \
						--overwrite_output_dir \
						--per_gpu_train_batch_size 4
```						
We used Google Colab for training the model,						