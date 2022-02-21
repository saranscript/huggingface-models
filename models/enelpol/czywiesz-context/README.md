---
language: pl
datasets:
- enelpol/czywiesz
---

# Model description

The model was created for selective question answering in Polish. I.e. it is used to find passages containing the answers to the given question.

It is used to encode the contexts (aka passages) in the DPR bi-encoder architecture. The architecture requires two separate models.
The question part has to be encoded with the corresponding [question encoder](https://huggingface.co/enelpol/czywiesz-question).

The model was created by fine-tuning [Herbert base cased](https://huggingface.co/allegro/herbert-base-cased) on "Czywiesz" dataset. 
[Czywiesz](https://clarin-pl.eu/dspace/handle/11321/39) dataset contains questions and Wikipedia articles extracted from the Polish Wikipedia.


# Usage

It is the easiest to use the model with the [Haystack framework](https://haystack.deepset.ai/overview/intro).

```python
from haystack.document_stores import FAISSDocumentStore
from haystack.retriever import DensePassageRetriever

document_store = FAISSDocumentStore(faiss_index_factory_str="Flat")

retriever = DensePassageRetriever(
    document_store=document_store,
    query_embedding_model="enelpol/czywiesz-question",
    passage_embedding_model="enelpol/czywiesz-context"
)

for document in documents:
    document_store.write_documents([document])
    
document_store.udpate_embeddings(retriever)
document_store.save("contexts.faiss")

```