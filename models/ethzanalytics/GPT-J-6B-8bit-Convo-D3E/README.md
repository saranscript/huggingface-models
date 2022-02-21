---

language:
- en
tags:
- text-generation
- gpt2
- gpt
license: mit
datasets:
- daily_dialog
widget:
- text: "I'm going to go use Colab like the description says cause this will error out"
  example_title: "use colab"
    

---
# GPT-J 6B (8-bit edition) - Daily Dialogues 3 Epoch

> essentially, we combine the workflow presented in the huggingface documentation [here](https://huggingface.co/docs/transformers/training) with the work done by Hivemind in fine-tuning [GPT-J-6B](https://huggingface.co/EleutherAI/gpt-j-6B) with limited memory. A detailed explanation of how it works can be found in [Hivemind's model card](https://huggingface.co/hivemind/gpt-j-6B-8bit).

-   trained for 3 epochs with a batch size of 4 on a modified version of the daily dialogues on a tesla V100
-   _note that some of this work is exploratory in nature and subject to being further improved through the Scientific Process_
-   Given the above and the fact that the classes for GPT-J are modified in-script, TBD whether it will work with huggingface inference API with the uploaded tokenizer etc.
-   Regardless, you can test it out with [this Colaboratory notebook](https://colab.research.google.com/gist/pszemraj/44a263c7bd22d24285b70fcb5717ad4d/gpt-j-6b-8bit-textgen-playground.ipynb)!

_Note: the model was trained with using "person &lt;greek_letter>" as a pseudo-BOS token for usage in the [ai-msgbot](https://github.com/pszemraj/ai-msgbot) project and subsequent training, say, on WhatsApp messages._

* * *

## Examples

### existence

    ==========Testing Prompt-ID #8 ==========
    PROMPT TEXT:
    person alpha:
    what is the meaning of existence?

    person beta:

    ----------FULL GENERATED TEXT:
    person alpha:
    what is the meaning of existence?

    person beta:
    does god exist?
    can one know what the creator wants?
    if the creator exists, does he need me?
    will the creator let me live after I

### "self-aware" named entity recognition

    ==========Testing Prompt-ID #1 ==========
    PROMPT TEXT:
    person alpha:
    what should I bring to the party?

    person beta:

    \----------FULL GENERATED TEXT:
    person alpha:
    what should I bring to the party?

    person beta:
    don’t bring anything

    the person alpha: can I borrow the person beta’s pants?
    the friend: sure
    person alpha and

* * *

    {'LR_scheduler_gamma': 0.6,
     '_n_gpu': 1,
     'adafactor': False,
     'adam_beta1': 0.9,
     'adam_beta2': 0.999,
     'adam_epsilon': 1e-08,
     'bf16': False,
     'bf16_full_eval': False,
     'configs_src': 'EleutherAI/gpt-j-6B',
     'data_tag': 'DailyDialogues',
     'dataloader_drop_last': False,
     'dataloader_num_workers': 0,
     'dataloader_pin_memory': True,
     'ddp_bucket_cap_mb': 'None',
     'ddp_find_unused_parameters': 'None',
     'debug': '[]',
     'deepspeed': 'None',
     'disable_tqdm': False,
     'do_eval': False,
     'do_predict': False,
     'do_train': False,
     'eval_accumulation_steps': 4,
     'eval_batch_size': 4,
     'eval_steps': 'None',
     'evaluation_strategy': 'no',
     'fp16': True,
     'fp16_backend': 'auto',
     'fp16_full_eval': True,
     'fp16_opt_level': 'O1',
     'gradient_accumulation_steps': 32,
     'gradient_checkpointing': True,
     'greater_is_better': 'None',
     'group_by_length': False,
     'half_precision_backend': 'amp',
     'hub_model_id': 'gpt-j-6B-8-bits_DS-DailyDialogues_Ep-3_Bs-4',
     'hub_strategy': 'every_save',
     'hub_token': '<HUB_TOKEN>',
     'ignore_data_skip': False,
     'label_names': 'None',
     'label_smoothing_factor': 0.0,
     'learning_rate': 1e-05,
     'length_column_name': 'length',
     'load_best_model_at_end': False,
     'local_rank': -1,
     'log_level': -1,
     'log_level_replica': -1,
     'log_on_each_node': True,
     'logging_dir': '/content/logs',
     'logging_first_step': False,
     'logging_nan_inf_filter': True,
     'logging_steps': 500,
     'logging_strategy': 'steps',
     'lr_scheduler_type': 'linear',
     'max_grad_norm': 0.5,
     'max_steps': -1,
     'metric_for_best_model': 'None',
     'model_src': 'hivemind/gpt-j-6B-8bit',
     'mp_parameters': '',
     'no_cuda': False,
     'num_train_epochs': 3,
     'output_dir': './checkpoints',
     'overwrite_output_dir': True,
     'past_index': -1,
     'per_device_eval_batch_size': 4,
     'per_device_train_batch_size': 4,
     'per_gpu_eval_batch_size': 'None',
     'per_gpu_train_batch_size': 'None',
     'prediction_loss_only': False,
     'push_to_hub': True,
     'push_to_hub_model_id': 'None',
     'push_to_hub_organization': 'None',
     'push_to_hub_token': '<PUSH_TO_HUB_TOKEN>',
     'remove_unused_columns': True,
     'report_to': "['tensorboard']",
     'resume_from_checkpoint': 'None',
     'run_name': './checkpoints',
     'save_on_each_node': False,
     'save_steps': 500,
     'save_strategy': 'epoch',
     'save_total_limit': 2,
     'seed': 42,
     'sharded_ddp': '[]',
     'skip_memory_metrics': True,
     'tf32': 'None',
     'tpu_metrics_debug': False,
     'tpu_num_cores': 'None',
     'train_batch_size': 4,
     'train_tag': '8-bits',
     'use_legacy_prediction_loop': False,
     'warmup_ratio': 0.0,
     'warmup_steps': 0,
     'weight_decay': 0,
     'xpu_backend': 'None'}
