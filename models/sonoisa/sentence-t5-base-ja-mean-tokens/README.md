---
language: ja
license: cc-by-sa-4.0
tags:
- sentence-transformers
- sentence-t5
- feature-extraction
- sentence-similarity
---


This is a Japanese sentence-T5 model.

日本語用Sentence-T5モデルです。

事前学習済みモデルとして[sonoisa/t5-base-japanese](https://huggingface.co/sonoisa/t5-base-japanese)を利用しました。  
推論の実行にはsentencepieceが必要です（pip install sentencepiece）。

手元の非公開データセットでは、精度は[sonoisa/sentence-bert-base-ja-mean-tokens](https://huggingface.co/sonoisa/sentence-bert-base-ja-mean-tokens)と同程度です。


# 使い方

```python
from transformers import T5Tokenizer, T5Model
import torch


class SentenceT5:
    def __init__(self, model_name_or_path, device=None):
        self.tokenizer = T5Tokenizer.from_pretrained(model_name_or_path)
        self.model = T5Model.from_pretrained(model_name_or_path).encoder
        self.model.eval()

        if device is None:
            device = "cuda" if torch.cuda.is_available() else "cpu"
        self.device = torch.device(device)
        self.model.to(device)

    def _mean_pooling(self, model_output, attention_mask):
        token_embeddings = model_output[0] #First element of model_output contains all token embeddings
        input_mask_expanded = attention_mask.unsqueeze(-1).expand(token_embeddings.size()).float()
        return torch.sum(token_embeddings * input_mask_expanded, 1) / torch.clamp(input_mask_expanded.sum(1), min=1e-9)

    @torch.no_grad()
    def encode(self, sentences, batch_size=8):
        all_embeddings = []
        iterator = range(0, len(sentences), batch_size)
        for batch_idx in iterator:
            batch = sentences[batch_idx:batch_idx + batch_size]

            encoded_input = self.tokenizer.batch_encode_plus(batch, padding="longest", 
                                           truncation=True, return_tensors="pt").to(self.device)
            model_output = self.model(**encoded_input)
            sentence_embeddings = self._mean_pooling(model_output, encoded_input["attention_mask"]).to('cpu')

            all_embeddings.extend(sentence_embeddings)

        return torch.stack(all_embeddings)


MODEL_NAME = "sonoisa/sentence-t5-base-ja-mean-tokens"
model = SentenceT5(MODEL_NAME)

sentences = ["暴走したAI", "暴走した人工知能"]
sentence_embeddings = model.encode(sentences, batch_size=8)

print("Sentence embeddings:", sentence_embeddings)
```
