# 🖼️ When ViT meets GPT-2 📝 

An image captioning model [ViT-GPT2](https://huggingface.co/flax-community/vit-gpt2/tree/main) by combining the ViT model and a French GPT2 model.

Part of the [Huggingface JAX/Flax event](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/).

The GPT2 model source code is modified so it can accept an encoder's output.
The pretained weights of both models are loaded, with a set of randomly initialized cross-attention weigths.
The model is trained on 65000 images from the COCO dataset for about 1500 steps (batch\_size=256), with the original English cpationis being translated to French for training purpose.

**Technical challenges**

- The source code of Flax's version of GPT-2 is modified to be able to accept an encoder's outputs, so it can be used as a decoder in an encoder-decoder architecture.

- Originally, we created [**FlaxViTGPT2ForConditionalGenerationModule**](https://huggingface.co/flax-community/vit-gpt2/blob/main/vit_gpt2/modeling_flax_vit_gpt2.py#L86), which is [**FlaxViTGPT2Module**](https://huggingface.co/flax-community/vit-gpt2/blob/main/vit_gpt2/modeling_flax_vit_gpt2.py#L28) (ViT + [GPT-2 without LM head]) with an extra LM head. However, when loading the pretrained French GPT-2 model, the LM head's weigths are not loaded. We therefore created [**FlaxViTGPT2LMForConditionalGenerationModule**](https://huggingface.co/flax-community/vit-gpt2/blob/main/vit_gpt2/modeling_flax_vit_gpt2_lm.py#L101) which is `ViT + [GPT-2 with LM head]`, and we no longer need to add a LM head over it. By doing so, the pretrained LM head's weights are also loaded, and the only randomly initialized weigths are the cross-attention weights.

- The provided training script `run_summarization.py` is modified to send pixel values to the model instead of a sequence of input token ids, and a necessary change due to the ViT model not accepting an `attention_mask` argument.

- We first tried to use [WIT : Wikipedia-based Image Text Dataset](https://github.com/google-research-datasets/wit), but found it is a very changeling task since, unlike traditional image captioning tasks, it requires the model to be able to generate different texts even if two images are similar (for example, two famous dogs might have completely different Wikipedia texts).

- We finally decided to use [COCO image dataset](https://cocodataset.org/#home) at the final day of this Flax community event. We were able to translate only about 65000 examples to French for training, and the model is trained for only 5 epochs (beyond this, it started to overfit). This leads to the poor performance. 

A HuggingFace Spaces demo for this model: [🖼️ French Image Captioning Demo 📝](https://huggingface.co/spaces/flax-community/image-caption-french)