Fine-tuning of `wav2vec2-base` on 100h of Librispeech training data. Results on "clean" data are very similar to the ones of the [official model](https://huggingface.co/facebook/wav2vec2-base-100h). However, the result on "other" is significantly worse - the model seems to have overfitting to the "clean" data.

Model was trained on *librispeech-clean-train.100* with following hyper-parameters:

- 2 GPUs Titan RTX
- Total update steps 13000
- Batch size per GPU: 32 corresponding to a *total batch size* of ca. ~1500 seconds
- Adam with linear decaying learning rate with 3000 warmup steps
- dynamic grouping for batch
- fp16
- attention_mask was **not** used during training

Check: https://wandb.ai/patrickvonplaten/huggingface/reports/Project-Dashboard--Vmlldzo1MDI2MTU?accessToken=69z0mrkoxs1msgh71p4nntr9shi6mll8rhtbo6c56yynygw0scp11d8z9o1xd0uk

*Result (WER)* on Librispeech test:

| "clean" | "other" |
|---|---|
| 6.5 | 18.7 |