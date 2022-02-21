---

tags:
- gpt2
- text-generation
- music-modeling
- music-generation

widget:
 - text: "PIECE_START"
 - text: "PIECE_START STYLE=JSFAKES GENRE=JSFAKES TRACK_START INST=48 BAR_START NOTE_ON=60"
 - text: "PIECE_START STYLE=JSFAKES GENRE=JSFAKES TRACK_START INST=48 BAR_START NOTE_ON=58"

---


# GPT-2 for Music

Language Models such as GPT-2 can be used for Music Generation. The idea is to represent pieces of music as texts, effectively reducing the task to Language Generation.

This model is a rather small instance of GPT-2 trained on [TristanBehrens/js-fakes-4bars](https://huggingface.co/datasets/TristanBehrens/js-fakes-4bars). The model generates 4 bars at a time of Bach-like chorales with four voices (soprano, alto, tenor, bass).

If you are contribute, if you want to say hello, if you want to know more, find me on [LinkedIn](https://www.linkedin.com/in/dr-tristan-behrens-734967a2/)

## Model description

The model is GPT-2 with 6 decoders and 8 attention-heads each. The context length is 512. The embedding dimensions are 512 as well. The vocabulary size is 119.

## Intended uses & limitations

This model is just a proof of concept. It shows that HuggingFace can be used to compose music.

### How to use

You can immediately start generating music running these lines of code:

```
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("TristanBehrens/js-fakes-4bars")
model = AutoModelForCausalLM.from_pretrained("TristanBehrens/js-fakes-4bars")

input_ids = tokenizer.encode("PIECE_START", return_tensors="pt")
print(input_ids)

generated_ids = model.generate(input_ids, max_length=500)
generated_sequence = tokenizer.decode(generated_ids[0])
print(generated_sequence)
```

Note that this just generates music as a text. In order to actually listen to the generated music, you can use this [notebook](https://huggingface.co/TristanBehrens/js-fakes-4bars/blob/main/colab_jsfakes_generation.ipynb).

### Limitations and bias

Since this model has been trained on a very small corpus of music, it is overfitting heavily. 

## Training data

The model has been trained on Omar Peracha's [JS Fake Chorales](https://github.com/omarperacha/js-fakes) dataset, which is a fine collection of 500 Bach-like chorales.