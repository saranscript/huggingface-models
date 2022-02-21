# GPT-Venus

(Me refers to puffy310)
Introducing GPT-Venus.... GPT-Venus is a large language model finetuned on me and my significant other's texts.

## Model description

GPT-Venus is a variant of the commonly used GPT-Neo, and as such is built of the huggingface implementation located at https://huggingface.co/EleutherAI/gpt-neo-125M as stated in the link before it has 125M params.

## Intended uses & limitations

I do not think it is necessary to state this, but this is the most useless version of GPT-Neo ever finetuned there is no intended use other than to poke fun at myself. Maybe it is good for something, I don't really know.

## How to use

Are you sure that you want to use this horrible model? If so, just use it in Transformers, or just the hosted inference API.

## Limitations and bias

It repeats everything, due to the limits of this small model, it also really has no generalization. The nature of my dataset also means it's not great with most questions. In a general EVAL such as https://github.com/EleutherAI/lm-evaluation-harness it would not do so well however I haven't fully tested that.

## Training data

How good do you really think a model can be using a bunch of texts from a guy and his girlfriend? Like really. It was trained on an augmented set of 5000 texts. After augmentation with https://github.com/makcedward/nlpaug it was multiplied by 160, more details are in the notebook

## Training procedure

I trained this on the Happy Transformers API. I used a notebook on colab, which is in the files. 

## Evaluation results

Eval Loss is 3.5971286296844482 from my custom benchmark, which is in notebooks/eval.txt, still have not used lm-eval-harness. This most likely won't give good results either way.

## Disclaimer

This is satire. Just like to poke fun at myself. I thought it would be fun.