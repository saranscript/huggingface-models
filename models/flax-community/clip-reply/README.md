# Searching Reaction GIFs with CLIP

![header gif](./assets/huggingface_explode3.png)

Reaction GIFs are an integral part of today's communication. They convey complex emotions with many levels, in a short compact format.

If a picture is worth a thousand words then a GIF is worth more.

We might even say that the level of complexity and expressiveness increases like:

`Emoji < Memes/Image < GIFs`

I think most people would agree it is not always easy to find the perfect reaction GIF. 

Although we started out with the more ambitious goal of GIF/Image generation we later settled on first finetuning CLIP. 
Which is needed to properly drive a generation model (like VQGAN). 

![header gif](./assets/main.gif)

Available CLIP models wouldn't be suitable to use without this finetuning as explained in the challenges below.

## 📝 Challenges

Classic (Image,Text) tasks like, image search, caption generation all focus on cases where the text is a description of the image.
This is mainly because large scale datasets available like COCO,WIT happen to be of that format. 
So it is interesting to see if models can also capture some more higher level relations.
like sentiment-> image mapping, where there is great variation on both sides.
We can think of reaction gif/images to be sentiment like, in fact the dataset we use was also gathered for sentiment analysis.
There is no one correct reaction GIF, which also makes evaluation challenging.

# Dataset

We use the [Reaction GIF dataset](https://github.com/bshmueli/ReactionGIF) by Shmueli et al. Also available in [datasets](https://huggingface.co/datasets/julien-c/reactiongif)(without the gifs, but I already had those files, nice coincidence 😉)
![Dataset](./assets/dataset.png)
We only use the tweet, GIF Response fields.
For this short experiment we only used the first frame of the GIFs to get generate the (text,image) pairs. Thought about using multiple frames from the GIF, but since there may not be much change between frames and didn't know how that would effect the already overfitting model. I decided to go with the simpler single frame version.

As opposed to other datasets, like COCO, we don't have multiple captions per image. Although same GIFs are used multiple times and we can modify the dataset that way we chose not to. Since we already had a very small dataset.

- Domain: Twitter
- Train size: 18,976
- Validation size: 351

# Model

We used the Hybrid CLIP model. Training script: [Hybrid CLIP](https://github.com/huggingface/transformers/blob/master/examples/research_projects/jax-projects/hybrid_clip/run_hybrid_clip.py) 

- Text Model: [twitter-roberta-base-emoji](https://huggingface.co/cardiffnlp/twitter-roberta-base-emoji)
- Vision Model: [openai/clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32)

## Different models tried

`cardiffnlp/twitter-roberta-base-*` models performed best compared to other text models; like the plain `roberta-base`, `bert-base-cased`.
This makes sense since this model is already trained on twitter data.

And among `cardiffnlp/twitter-roberta-base-*` models `twitter-roberta-base-emoji` performed best. (As I had hoped)
This model is `cardiffnlp/twitter-roberta-base` further fine-tuned on emoji classification task, which we can say (emojis) is a parallel to GIFs. 

Also tried `google/vit-base-patch32-384`, `google/vit-base-patch16-384` for the vision models, but results were inconclusive.

## Result Interpretation (Warning)

It would be wrong to claim that this model learned 'semantic reasoning' between sentence and image features. 

It more likely learned a mapping between sentence sentiment and image occurrence statistics. Because the set of gif images repeat across the dataset, although paired with different sentences.

That is not to say that learning such semantic relations isn't feasible with this model. And it is well worth working on in the future, with a larger and better constructed dataset.

### 📈 Training Logs

Training logs can be found [here](https://wandb.ai/cceyda/flax-clip?workspace=user-cceyda)
It was really easy to overfit since it was a tiny dataset. Used early stopping.
Other parameters:
```
--max_seq_length 128 \
--per_device_train_batch_size="32" \
--learning_rate="1e-5" 
--warmup_steps="150" 
```

# 💡 Future Potential

It is possible to generate a very large training set by scraping twitter.(Couldn't do during the event because of twitter rate limit)

I found it surprising how well the results turned out to be with so little data and training time. Although it is really hard to define what is an appropriate reaction image, and there are definite mistakes model makes.

(I also trained just a plain clip but didn't have time to prep demo for that 😅 which was also similarly over fitting and only had time to do a single run)

I will definitely be trying out training a similar model for emoji & meme data.

Training CLIP is just the first step, if we have a well trained CLIP generation is within reach 🚀   

# How to use
The final model available [here](https://huggingface.co/ceyda/clip-reply)

```py
from model import FlaxHybridCLIP # see demo 
from transformers import AutoTokenizer, CLIPProcessor

model = FlaxHybridCLIP.from_pretrained("ceyda/clip-reply")
processor = CLIPProcessor.from_pretrained("openai/clip-vit-base-patch32")
processor.tokenizer = AutoTokenizer.from_pretrained("cardiffnlp/twitter-roberta-base")

def query(image_paths,query_text):
    images = [Image.open(im).convert("RGB") for im in image_paths]
    inputs = processor(text=[query_text], images=images, return_tensors="jax", padding=True)
    inputs["pixel_values"] = jnp.transpose(inputs["pixel_values"], axes=[0, 2, 3, 1])
    outputs = model(**inputs)
    logits_per_image = outputs.logits_per_image.reshape(-1)
    probs = jax.nn.softmax(logits_per_image)
```

# Created By

Ceyda Cinarel [@ceyda](https://huggingface.co/ceyda)

Made during the flax community [event](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104/58)

# TL;DR The task

Input: Some sentence (like a tweet)
Output: The most suitable reaction GIF image (Ranking)

Example: 
  - Input: I miss you 
  - Output: ![hug](./assets/example_gif.jpg)
  
# Demo

https://huggingface.co/spaces/flax-community/clip-reply-demo


