---
language: 
- en
tags:
- t5
- analysis
- book
- notes
datasets:
- kmfoda/booksum
metrics:
- rouge

widget:
- text: "A large drop of sun lingered on the horizon and then dripped over and was gone, and the sky was brilliant over the spot where it had gone, and a torn cloud, like a bloody rag, hung over the spot of its going. And dusk crept over the sky from the eastern horizon, and darkness crept over the land from the east."
  example_title: "grapes of wrath"
- text: "The year was 2081, and everybody was finally equal. They weren't only equal before God and the law. They were equal every which way. Nobody was smarter than anybody else. Nobody was better looking than anybody else. Nobody was stronger or quicker than anybody else. All this equality was due to the 211th, 212th, and 213th Amendments to the Constitution, and to the unceasing vigilance of agents of the United States Handicapper General."
  example_title: "Harrison Bergeron"
- text: "The ledge, where I placed my candle, had a few mildewed books piled up in one corner; and it was covered with writing scratched on the paint. This writing, however, was nothing but a name repeated in all kinds of characters, large and small—Catherine Earnshaw, here and there varied to Catherine Heathcliff, and then again to Catherine Linton. In vapid listlessness I leant my head against the window, and continued spelling over Catherine Earnshaw—Heathcliff—Linton, till my eyes closed; but they had not rested five minutes when a glare of white letters started from the dark, as vivid as spectres—the air swarmed with Catherines; and rousing myself to dispel the obtrusive name, I discovered my candle wick reclining on one of the antique volumes, and perfuming the place with an odour of roasted calf-skin."
  example_title: "Wuthering Heights"
  
inference:
  parameters:
    no_repeat_ngram_size: 2
    max_length: 32
    early_stopping: True
---

# Semantic Analysis with T5 - Size L

- **NOTE: this is fairly intensive computationally and recommended to be run on GPU. Take a look at [this demo on Google Colab](https://colab.research.google.com/gist/pszemraj/5760325192a37a7549cd666e473a1823/example-t5-v1_1-l-semantic-analyzer.ipynb) for examples**

This model is a fine-tuned version of [google/t5-v1_1-large](https://huggingface.co/google/t5-v1_1-large) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0546


## Short Example

- INPUT:
> Carmen: We're kids, not monsters. Dr Romero: What's the difference?
- OUTPUT:
> in this chapter. Dr Romero: What's the difference? We're kids, not monsters. The narrator says, "I'm not a monster; I've never seen anything like it before." This is an important question for the audience to consider as they decide whether or not to go on with the story. Carmen: We don't even know what we are talking about when we talk about the differences between childhood and adulthood. She knows that children are more likely to grow up than adults.

## Model description

- `booksum` is a dataset created primarily for long-range summarization. It's excellent at that, and usually this is done with the `chapter` and `summary_text` columns. However, there is a `summary_analysis` column as well, containing literary analysis on the passage in question :eyes:
- this model was trained on text-to-text with `summary_text` as the input and `summary_analysis` as the output, so it will analyze whatever text for _deeper meaning_.


## Intended uses & limitations

- text in the English language goes in, literary analysis comes out.

## Training and evaluation data

```
{'epoch': 4.0,
 'eval_gen_len': 127.0,
 'eval_loss': 2.0544395446777344,
 'eval_rouge1': 22.7763,
 'eval_rouge2': 4.7556,
 'eval_rougeL': 12.486,
 'eval_rougeLsum': 21.2261,
 'eval_runtime': 223.5668,
 'eval_samples_per_second': 0.564,
 'eval_steps_per_second': 0.036}
 ```

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 4e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- distributed_type: multi-GPU
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.03
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 14.3171       | 1.0   | 332  | 14.9743         |
| 2.7203        | 2.0   | 664  | 2.4602          |
| 2.3278        | 3.0   | 996  | 2.1239          |
| 2.1264        | 4.0   | 1328 | 2.0546          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.2+cu113
- Datasets 1.18.3
- Tokenizers 0.11.0

# Extended Analysis

- A detailed analysis of the [Rick & Morty copypasta](https://knowyourmeme.com/memes/to-be-fair-you-have-to-have-a-very-high-iq-to-understand-rick-and-morty) is provided here for you, free of charge:

> The narrator's description of Rick and Morty is one of the most intelligent people in the world. They have an extremely high IQ, but they are idiots who dislike the show because they lack the intellectual capacity to understand the jokes about their comedy. In fact, there are even more stupid people who hate this show- which makes them seem to be so clever that they do not know anything about it. Even though they don't get much insight into the nature of these characters; they cannot appreciate the depths of Dickens: "Wubba Lubba Dubdub" refers to the Russian epic Fathers and Sons. This is also a reference to Narodna Volya volyevity. It was written by Dan Harmon himself. He has no idealism. As he does not just want to see something deeper than anyone else. I amusement at allusion to his own philosophy. For example, however, as if you were born in Russia. However, we can only look at any way backward perspective on life. Indeed, for some readers will never really understand what exactly what they thinkers would rather than simply laugh at him. And yes, when i say, "Why? Why?"? That're actually means "I love me!" Rather than laugh out loudly laughing at the absurdity of my mind. But why do you like to laugh with such humour? What fools? Does it make you laugh? Do you find it funny? Are you smart enough to accept it? Did you believe that it'll go over your head? Or did you try to figure out how ridiculous it is going on? Will you ask yourself? Can you tell me? If you've got it wrong? Well, then, perhaps you should take it seriously? Of course, you ought to question whether or not. No matter how silly you might react? Would you consider it too far too late? You may wonder why you feel so foolish? How could you respond? So many critics have been misinterpreserved? Oh, after all, please note that Mr. Glossary! Chesnutt seems to suggest that CHAPTER 5 QUOfolishness? Ack &#5 / Whereaslepated? To put it aside from the end of Chapter 7? There are several other examples of comic genius? These are very difficult to decipherence? Just as well as the rest of our society? Were aware of this kind of humor? Hey, let us know that the universe is full of irony? On the other hand, Dr. Jeky knows everything about human beings around us? At the same time, Doctor Jessey uses the word "Rick and Mrs. Jonah". Also, Rosie suggests that she wants to give up her witty commentary on the existence of humanity itself. One must remember that every single sentence contains multiple references to non-fictional references throughout the novel. Another example is the use of language used to describe the relationship between man and Manette. She believes that humans are capable of expressing themselves in terms of self-destructiveness and morality, and yet another reason for rejecting certain aspects of science and religion. When she says "Nothing," she points out that those words are meant to represent the real worldview of reality. Furthermore, Richardson writes that "the whole thing is called "The Book of Life" and "A Tale of Two Cities"- referring to various forms of metaphors, including the phrase "Dickengenev." Similarly, the tattoo is referred to as part of Frankensteinism, suggesting that its meaning lies in relation to Christianity. Yet again, since it comes from two different contexts associated with each other. Like the book, it takes place in order to illustrate the difference between the two books and the storyliness contained within the second half of both novels and literature. Although the title of Jerry Cruneshadows the readership of Cyranonism and Romance. Not only does it come from scratching the face of Stevenson and Turgenovation. From the opening lines of Babbithorne, Riddlecliffe draws heavily upon the image of Jesus Christ, Godwine describes the character of Death.