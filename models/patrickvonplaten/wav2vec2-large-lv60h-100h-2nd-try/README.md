Fine-tuning of `wav2vec2-large-lv60` on 100h of Librispeech training data. Results are a bit worse than those reported in the Appendix in Table 3 of the original [paper](https://arxiv.org/pdf/2006.11477.pdf).

Model was trained on *librispeech-clean-train.100* with following hyper-parameters:

- 2 GPUs Titan RTX
- Total update steps 17500
- Batch size per GPU: 16 corresponding to a *total batch size* of ca. ~750 seconds
- Adam with linear decaying learning rate with 3000 warmup steps
- dynamic padding for batch
- fp16
- attention_mask was used during training

Check: https://wandb.ai/patrickvonplaten/huggingface/reports/Project-Dashboard--Vmlldzo0OTI0OTc?accessToken=8azw8iyxnbiqd4ytxcgm4hbnfh3x1b2c9l2eyfqfzdqw7l0icreljc9qpx0rkl6f

*Result (WER)* on Librispeech test:

| "clean" | "other" |
|---|---|
| 4.0 | 10.3 |