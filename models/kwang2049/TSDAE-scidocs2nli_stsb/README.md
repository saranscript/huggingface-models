# kwang2049/TSDAE-scidocs2nli_stsb
This is a model from the paper ["TSDAE: Using Transformer-based Sequential Denoising Auto-Encoder for Unsupervised Sentence Embedding Learning"](https://arxiv.org/abs/2104.06979). This model adapts the knowledge from the NLI and STSb data to the specific domain scidocs. Training procedure of this model:
 1. Initialized with [bert-base-uncased](https://huggingface.co/bert-base-uncased);
 2. Unsupervised training on scidocs with the TSDAE objective;
 3. Supervised training on the NLI data with cross-entropy loss;
 4. Supervised training on the STSb data with MSE loss.
 
 The pooling method is CLS-pooling.
 
 ## Usage
 To use this model, an convenient way is through [SentenceTransformers](https://github.com/UKPLab/sentence-transformers). So please install it via:
 ```bash
 pip install sentence-transformers
 ```
 And then load the model and use it to encode sentences:
 ```python
 from sentence_transformers import SentenceTransformer, models
 dataset = 'scidocs'
 model_name_or_path = f'kwang2049/TSDAE-{dataset}2nli_stsb'
 model = SentenceTransformer(model_name_or_path)
 model[1] = models.Pooling(model[0].get_word_embedding_dimension(), pooling_mode='cls')  # Note this model uses CLS-pooling
 sentence_embeddings = model.encode(['This is the first sentence.', 'This is the second one.'])
 ```
 ## Evaluation
 To evaluate the model against the datasets used in the paper, please install our evaluation toolkit [USEB](https://github.com/UKPLab/useb):
 ```bash
 pip install useb  # Or git clone and pip install .
 python -m useb.downloading all  # Download both training and evaluation data
 ```
 And then do the evaluation:
 ```python
 from sentence_transformers import SentenceTransformer, models
import torch
from useb import run_on
dataset = 'scidocs'
model_name_or_path = f'kwang2049/TSDAE-{dataset}2nli_stsb'
model = SentenceTransformer(model_name_or_path)
model[1] = models.Pooling(model[0].get_word_embedding_dimension(), pooling_mode='cls')  # Note this model uses CLS-pooling
@torch.no_grad()
def semb_fn(sentences) -> torch.Tensor:
    return torch.Tensor(model.encode(sentences, show_progress_bar=False))
result = run_on(
    dataset,
    semb_fn=semb_fn,
    eval_type='test',
    data_eval_path='data-eval'
)
 ```
 
 ## Training
 Please refer to [the page of TSDAE training](https://github.com/UKPLab/sentence-transformers/tree/master/examples/unsupervised_learning/TSDAE) in SentenceTransformers.
 
 ## Cite & Authors
 If you use the code for evaluation, feel free to cite our publication [TSDAE: Using Transformer-based Sequential Denoising Auto-Encoderfor Unsupervised Sentence Embedding Learning](https://arxiv.org/abs/2104.06979):
```bibtex 
@article{wang-2021-TSDAE,
    title = "TSDAE: Using Transformer-based Sequential Denoising Auto-Encoderfor Unsupervised Sentence Embedding Learning",
    author = "Wang, Kexin and Reimers, Nils and  Gurevych, Iryna", 
    journal= "arXiv preprint arXiv:2104.06979",
    month = "4",
    year = "2021",
    url = "https://arxiv.org/abs/2104.06979",
}
```