---

language:
- en
tags:
- summarization
- bigbig_pegasus_
- pegasus
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

inference:
  parameters:
    max_length: 64
    no_repeat_ngram_size: 3
    do_sample: True
    top_p: 0.95
    repetition_penalty: 3.7
    num_beams : 4
    

---

# bigbird pegasus on the booksum dataset- 40,000 steps

>the fully-tuned model can be found [here](https://huggingface.co/pszemraj/bigbird-pegasus-large-K-booksum). This checkpoint will stay live because the summarization is almost as good and compute is way faster.

- typical datasets for summarization models arePubMed / arXiv; for my use cases I have found these to be not very useful 
  - summarizing text via arXiv models will typically make the summary sound so needlessly complicated you might as well have read the original text in that time anyway.
  - this model is one attempt to help with that 
- this is not a finished checkpoint but WIP: 
    - 40K steps or 4 epochs trained on the booksum dataset (have gone through  ~60-70% of the training dataset). 
    - Note that while the model started from continues to be able to apply the attention mechanism at 4096 tokens, it was trained with the dataset tokenized to a `max_length` of 1024 for GPU memory reasons.
    - Will continue to improve based on any result findings/feedback.
- the starting checkpoint was `google/bigbird-pegasus-large-bigpatent`

# example usage

> An extended example, including a demo of batch summarization, is [here](https://colab.research.google.com/gist/pszemraj/2c8c0aecbcd4af6e9cbb51e195be10e2/bigbird-pegasus-large-booksum-20k-example.ipynb).

- create the summarizer object:

```
from transformers import AutoModelForSeq2SeqLM, AutoTokenizer
from transformers import pipeline

_model = AutoModelForSeq2SeqLM.from_pretrained(
                "pszemraj/bigbird-pegasus-large-booksum-40k-K",
                low_cpu_mem_usage=True,
            )

_tokenizer = AutoTokenizer.from_pretrained(
                "pszemraj/bigbird-pegasus-large-booksum-40k-K"
            )
                                           

summarizer = pipeline(
                    "summarization", 
                    model=_model, 
                    tokenizer=_tokenizer
                )
             
 ```

- define text to be summarized, and pass it through the pipeline. Boom done. 

```
wall_of_text = "your text to be summarized goes here."

result = summarizer(
           wall_of_text,
           min_length=16, 
           max_length=256,
           no_repeat_ngram_size=3, 
           clean_up_tokenization_spaces=True,
    )

print(result[0]['summary_text'])
```


# Results

- below are scores from running evaluation on the entire Validation set, around ~1400 rows.
- note that while the dataset has three subsets (chapter, book, paragraph) - see the [paper](https://arxiv.org/abs/2105.08209). the scores below are run in aggregate
- seems that these scores are on par / slightly better than what was reported in the paper, still more validation and other work to do.

```
{
    "eval_gen_len": 126.5815,
    "eval_loss": 3.747079610824585,
    "eval_rouge1": 30.4775,
    "eval_rouge2": 4.8919,
    "eval_rougeL": 16.742,
    "eval_rougeLsum": 27.57,
    "eval_runtime": 4246.9369,
    "eval_samples_per_second": 0.349,
    "eval_steps_per_second": 0.349
}
```
