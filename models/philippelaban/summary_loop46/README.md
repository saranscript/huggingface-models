---
language:
- en
tags:
- summarization
license: apache-2.0
datasets:
- cnn_dailymail
metrics:
- rouge
---

# Try out in the Hosted inference API

In the right panel, you can try to the model (although it only handles a short sequence length).
Enter the document you want to summarize in the panel on the right.

# Model Loading
The model (based on a GPT2 base architecture) can be loaded in the following way:
```
from transformers import GPT2LMHeadModel, GPT2TokenizerFast

model = GPT2LMHeadModel.from_pretrained("philippelaban/summary_loop46")
tokenizer = GPT2TokenizerFast.from_pretrained("philippelaban/summary_loop46")
```

# Example Use
```
document = "Bouncing Boulders Point to Quakes on Mars. A preponderance of boulder tracks on the red planet may be evidence of recent seismic activity. If a rock falls on Mars, and no one is there to see it, does it leave a trace? Yes, and it's a beautiful herringbone-like pattern, new research reveals. Scientists have now spotted thousands of tracks on the red planet created by tumbling boulders. Delicate chevron-shaped piles of Martian dust and sand frame the tracks, the team showed, and most fade over the course of a few years. Rockfalls have been spotted elsewhere in the solar system, including on the moon and even a comet. But a big open question is the timing of these processes on other worlds — are they ongoing or did they predominantly occur in the past?"

tokenized_document = tokenizer([document], max_length=300, truncation=True, return_tensors="pt")["input_ids"].cuda()
input_shape = tokenized_document.shape
outputs = model.generate(tokenized_document, do_sample=False, max_length=500, num_beams=4, num_return_sequences=4, no_repeat_ngram_size=6, return_dict_in_generate=True, output_scores=True)
candidate_sequences = outputs.sequences[:, input_shape[1]:] # Remove the encoded text, keep only the summary
candidate_scores = outputs.sequences_scores.tolist()

for candidate_tokens, score in zip(candidate_sequences, candidate_scores):
    summary = tokenizer.decode(candidate_tokens)
    print("[Score: %.3f] %s" % (score, summary[:summary.index("END")]))
```

# Example output
```
[Score: -0.153]  These tracks have been spotted elsewhere on Mars. If a rockfalls on Mars has been spotted elsewhere on the red planet. Scientists have spotted thousands of tracks on Mars. A rockfalls on Mars have been spotted elsewhere on the Red Planet.
[Score: -0.154]  These tracks have been spotted elsewhere on Mars. If a rockfalls on Mars has been spotted elsewhere on the red planet. Scientists have spotted thousands of tracks on Mars. A rockfalls on Mars have been spotted elsewhere on the planet.
[Score: -0.154]  These tracks have been spotted elsewhere on Mars. If a rockfalls on Mars has been spotted elsewhere on the red planet. Scientists have spotted thousands of tracks on Mars. A rockfalls have been spotted elsewhere on the Red Planet.
[Score: -0.195]  These tracks have been spotted elsewhere on Mars. If a rockfalls on Mars has been spotted elsewhere on the red planet. Scientists have spotted thousands of tracks on Mars. A rockfalls on Mars have been spotted elsewhere on the Red Planet. A rockfalls have been spotted everywhere on the red planet.
```

# Github repo

You can access more information, access to the scoring function, the training script, or an example training log on the Github repo: https://github.com/CannyLab/summary_loop