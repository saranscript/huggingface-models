---

language:
- en
tags:
- summarization
- led
- summary
- longformer
license: apache-2.0
datasets:
- kmfoda/booksum
metrics:
- rouge
widget:
- text: "large earthquakes along a given fault segment do not occur at random intervals because it takes time to accumulate the strain energy for the rupture. The rates at which tectonic plates move and accumulate strain at their boundaries are approximately uniform. Therefore, in first approximation, one may expect that large ruptures of the same fault segment will occur at approximately constant time intervals. If subsequent main shocks have different amounts of slip across the fault, then the recurrence time may vary, and the basic idea of periodic mainshocks must be modified. For great plate boundary ruptures the length and slip often vary by a factor of 2. Along the southern segment of the San Andreas fault the recurrence interval is 145 years with variations of several decades. The smaller the standard deviation of the average recurrence interval, the more specific could be the long term prediction of a future mainshock."
  example_title: "earthquakes"
- text: " A typical feed-forward neural field algorithm. Spatiotemporal coordinates are fed into a neural network that predicts values in the reconstructed domain. Then, this domain is mapped to the sensor domain where sensor measurements are available as supervision. Class and Section Problems Addressed Generalization (Section 2) Inverse problems, ill-posed problems, editability; symmetries. Hybrid Representations (Section 3) Computation & memory efficiency, representation capacity, editability: Forward Maps (Section 4) Inverse problems Network Architecture (Section 5) Spectral bias, integration & derivatives. Manipulating Neural Fields (Section 6) Edit ability, constraints, regularization. Table 2: The five classes of techniques in the neural field toolbox each addresses problems that arise in learning, inference, and control. (Section 3). We can supervise reconstruction via differentiable forward maps that transform Or project our domain (e.g, 3D reconstruction via 2D images; Section 4) With appropriate network architecture choices, we can overcome neural network spectral biases (blurriness) and efficiently compute derivatives and integrals (Section 5). Finally, we can manipulate neural fields to add constraints and regularizations, and to achieve editable representations (Section 6). Collectively, these classes constitute a 'toolbox' of techniques to help solve problems with neural fields There are three components in a conditional neural field: (1) An encoder or inference function € that outputs the conditioning latent variable 2 given an observation 0 E(0) =2. 2 is typically a low-dimensional vector, and is often referred to aS a latent code Or feature code_ (2) A mapping function 4 between Z and neural field parameters O: Y(z) = O; (3) The neural field itself $. The encoder € finds the most probable z given the observations O: argmaxz P(2/0). The decoder maximizes the inverse conditional probability to find the most probable 0 given Z: arg- max P(Olz). We discuss different encoding schemes with different optimality guarantees (Section 2.1.1), both global and local conditioning (Section 2.1.2), and different mapping functions Y (Section 2.1.3) 2. Generalization Suppose we wish to estimate a plausible 3D surface shape given a partial or noisy point cloud. We need a suitable prior over the sur- face in its reconstruction domain to generalize to the partial observations. A neural network expresses a prior via the function space of its architecture and parameters 0, and generalization is influenced by the inductive bias of this function space (Section 5)."
  example_title: "scientific paper"
- text: " the big variety of data coming from diverse sources is one of the key properties of the big data phenomenon. It is, therefore, beneficial to understand how data is generated in various environments and scenarios, before looking at what should be done with this data and how to design the best possible architecture to accomplish this The evolution of IT architectures, described in Chapter 2, means that the data is no longer processed by a few big monolith systems, but rather by a group of services In parallel to the processing layer, the underlying data storage has also changed and became more distributed This, in turn, required a significant paradigm shift as the traditional approach to transactions (ACID) could no longer be supported. On top of this, cloud computing is becoming a major approach with the benefits of reducing costs and providing on-demand scalability but at the same time introducing concerns about privacy, data ownership, etc In the meantime the Internet continues its exponential growth: Every day both structured and unstructured data is published and available for processing: To achieve competitive advantage companies have to relate their corporate resources to external services, e.g. financial markets, weather forecasts, social media, etc While several of the sites provide some sort of API to access the data in a more orderly fashion; countless sources require advanced web mining and Natural Language Processing (NLP) processing techniques: Advances in science push researchers to construct new instruments for observing the universe O conducting experiments to understand even better the laws of physics and other domains. Every year humans have at their disposal new telescopes, space probes, particle accelerators, etc These instruments generate huge streams of data, which need to be stored and analyzed. The constant drive for efficiency in the industry motivates the introduction of new automation techniques and process optimization: This could not be done without analyzing the precise data that describe these processes. As more and more human tasks are automated, machines provide rich data sets, which can be analyzed in real-time to drive efficiency to new levels. Finally, it is now evident that the growth of the Internet of Things is becoming a major source of data. More and more of the devices are equipped with significant computational power and can generate a continuous data stream from their sensors. In the subsequent sections of this chapter, we will look at the domains described above to see what they generate in terms of data sets. We will compare the volumes but will also look at what is characteristic and important from their respective points of view. 3.1 The Internet is undoubtedly the largest database ever created by humans. While several well described; cleaned, and structured data sets have been made available through this medium, most of the resources are of an ambiguous, unstructured, incomplete or even erroneous nature. Still, several examples in the areas such as opinion mining, social media analysis, e-governance, etc, clearly show the potential lying in these resources. Those who can successfully mine and interpret the Internet data can gain unique insight and competitive advantage in their business An important area of data analytics on the edge of corporate IT and the Internet is Web Analytics."
  example_title: "data science textbook"
- text: "Transformer-based models have shown to be very useful for many NLP tasks. However, a major limitation of transformers-based models is its O(n^2)O(n 
2) time & memory complexity (where nn is sequence length). Hence, it's computationally very expensive to apply transformer-based models on long sequences n > 512n>512. Several recent papers, e.g. Longformer, Performer, Reformer, Clustered attention try to remedy this problem by approximating the full attention matrix. You can checkout 🤗's recent blog post in case you are unfamiliar with these models.

BigBird (introduced in paper) is one of such recent models to address this issue. BigBird relies on block sparse attention instead of normal attention (i.e. BERT's attention) and can handle sequences up to a length of 4096 at a much lower computational cost compared to BERT. It has achieved SOTA on various tasks involving very long sequences such as long documents summarization, question-answering with long contexts.

BigBird RoBERTa-like model is now available in 🤗Transformers. The goal of this post is to give the reader an in-depth understanding of big bird implementation & ease one's life in using BigBird with 🤗Transformers. But, before going into more depth, it is important to remember that the BigBird's attention is an approximation of BERT's full attention and therefore does not strive to be better than BERT's full attention, but rather to be more efficient. It simply allows to apply transformer-based models to much longer sequences since BERT's quadratic memory requirement quickly becomes unbearable. Simply put, if we would have ∞ compute & ∞ time, BERT's attention would be preferred over block sparse attention (which we are going to discuss in this post).

If you wonder why we need more compute when working with longer sequences, this blog post is just right for you!

Some of the main questions one might have when working with standard BERT-like attention include:

Do all tokens really have to attend to all other tokens?
Why not compute attention only over important tokens?
How to decide what tokens are important?
How to attend to just a few tokens in a very efficient way?
In this blog post, we will try to answer those questions.

What tokens should be attended to?
We will give a practical example of how attention works by considering the sentence 'BigBird is now available in HuggingFace for extractive question answering'. In BERT-like attention, every word would simply attend to all other tokens.

Let's think about a sensible choice of key tokens that a queried token actually only should attend to by writing some pseudo-code. Will will assume that the token available is queried and build a sensible list of key tokens to attend to.

>>> # let's consider following sentence as an example
>>> example = ['BigBird', 'is', 'now', 'available', 'in', 'HuggingFace', 'for', 'extractive', 'question', 'answering']

>>> # further let's assume, we're trying to understand the representation of 'available' i.e. 
>>> query_token = 'available'
>>> # We will initialize an empty `set` and fill up the tokens of our interest as we proceed in this section.
>>> key_tokens = [] # => currently 'available' token doesn't have anything to attend
Nearby tokens should be important because, in a sentence (sequence of words), the current word is highly dependent on neighboring past & future tokens. This intuition is the idea behind the concept of sliding attention."
  example_title: "bigbird blog intro"
  
inference:
  parameters:
    max_length: 64
    min_length: 4
    no_repeat_ngram_size: 2
    early_stopping: True
    repetition_penalty: 2.4
    length_penalty: 0.5
    encoder_no_repeat_ngram_size : 3
    num_beams : 4
    

---

# Longformer Encoder-Decoder (LED) fine-tuned on Booksum

- `allenai/led-base-16384` checkpoint trained on the [booksum dataset](https://arxiv.org/abs/2105.08209) for 3 epochs.
- handles summarization a-la "school notes" style well, but takes a while to run (even compared to larger models such as a  [bigbird-pegasus](https://huggingface.co/pszemraj/bigbird-pegasus-large-booksum-40k-K) checkpoint on the same data.
- upside: works well on lots of text, can hand 16384 tokens/batch.
  - an example usage notebook is [here](https://colab.research.google.com/gist/pszemraj/da8872e702ea9e3d74c39a236e89104b/led-base-booksum-example.ipynb) with details
  
## Other Checkpoints on Booksum

- A one-epoch version of [LED-large is available here](https://huggingface.co/pszemraj/led-large-book-summary-1E) - a more polished version still WIP.

---

# Usage - Basics

- from testing, it is highly recommended to use the parameter `encoder_no_repeat_ngram_size=3` when calling the pipeline object. 
  - this forces the model to use new vocabulary and create an abstractive summary, as at times it will compile the best _extractive_ summary from the input provided.
- create the pipeline object:

```
from transformers import AutoModelForSeq2SeqLM, AutoTokenizer
from transformers import pipeline

hf_name = 'pszemraj/led-base-16384-finetuned-booksum'

_model = AutoModelForSeq2SeqLM.from_pretrained(
                hf_name,
                low_cpu_mem_usage=True,
            )

_tokenizer = AutoTokenizer.from_pretrained(
                hf_name
            )
                                           

summarizer = pipeline(
                    "summarization", 
                    model=_model, 
                    tokenizer=_tokenizer
                )
```

- put words into the pipeline object:

```
wall_of_text = "your words here"

result = summarizer(
           wall_of_text,
           min_length=16, 
           max_length=256,
           no_repeat_ngram_size=3, 
           encoder_no_repeat_ngram_size =3,
           clean_up_tokenization_spaces=True,
           repetition_penalty=3.7,
           num_beams=4,
           early_stopping=True,
    )


```

---


# Results

- evaluation was completed with the following params and received the following score

- params:

```
# set generate hyperparameters
model.config.num_beams = 5
model.config.max_length = 512
model.config.min_length = 32
model.config.length_penalty = 3.5
model.config.early_stopping = True
model.config.no_repeat_ngram_size = 3

trainer.evaluate(num_beams=5, max_length=128)
```

- scores (on 1/10 validation for RT reasons):

```
  {'eval_loss': 2.899840831756592,
   'eval_rouge1': 30.0761, 
   'eval_rouge2': 6.4964, 
   'eval_rougeL': 15.9819, 
   'eval_rougeLsum': 28.2764, 
   'eval_gen_len': 126.8514, 
   'eval_runtime': 1442.991, 
   'eval_samples_per_second': 0.103,
   'eval_steps_per_second': 0.103
 }

```

---