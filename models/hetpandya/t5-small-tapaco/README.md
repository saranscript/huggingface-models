---
language: en
datasets:
- tapaco
---
# T5-small for paraphrase generation

Google's T5 small fine-tuned on [TaPaCo](https://huggingface.co/datasets/tapaco) dataset for paraphrasing.

## Model in Action 🚀

```python
from transformers import T5ForConditionalGeneration, T5Tokenizer

tokenizer = T5Tokenizer.from_pretrained("hetpandya/t5-small-tapaco")
model = T5ForConditionalGeneration.from_pretrained("hetpandya/t5-small-tapaco")

def get_paraphrases(sentence, prefix="paraphrase: ", n_predictions=5, top_k=120, max_length=256,device="cpu"):
        text = prefix + sentence + " </s>"
        encoding = tokenizer.encode_plus(
            text, pad_to_max_length=True, return_tensors="pt"
        )
        input_ids, attention_masks = encoding["input_ids"].to(device), encoding[
            "attention_mask"
        ].to(device)

        model_output = model.generate(
            input_ids=input_ids,
            attention_mask=attention_masks,
            do_sample=True,
            max_length=max_length,
            top_k=top_k,
            top_p=0.98,
            early_stopping=True,
            num_return_sequences=n_predictions,
        )

        outputs = []
        for output in model_output:
            generated_sent = tokenizer.decode(
                output, skip_special_tokens=True, clean_up_tokenization_spaces=True
            )
            if (
                generated_sent.lower() != sentence.lower()
                and generated_sent not in outputs
            ):
                outputs.append(generated_sent)
        return outputs

paraphrases = get_paraphrases("The house will be cleaned by me every Saturday.")

for sent in paraphrases:
  print(sent)
```

## Output
```
The house is cleaned every Saturday by me.
The house will be cleaned on Saturday.
I will clean the house every Saturday.
I get the house cleaned every Saturday.
I will clean this house every Saturday.
```

## Model fine-tuning
Please find my guide on fine-tuning the model here:

https://towardsdatascience.com/training-t5-for-paraphrase-generation-ab3b5be151a2


Created by [Het Pandya/@hetpandya](https://github.com/hetpandya) | [LinkedIn](https://www.linkedin.com/in/het-pandya)

Made with <span style="color: red;">&hearts;</span> in India