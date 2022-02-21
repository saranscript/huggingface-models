# GPT2 Keyword Based Lecture Generator

## Model description

GPT2 fine-tuned on the TED Talks Dataset (published under the Creative Commons BY-NC-ND license).

## Intended uses

Used to generate spoken-word lectures.

### How to use

Input text: 

          <BOS> title <|SEP|> Some keywords <|SEP|>

Keyword Format: "Main Topic"."Subtopic1","Subtopic2","Subtopic3"

Code Example:
```
prompt = <BOS> + title + \\
         <|SEP|> + keywords + <|SEP|>
         
generated = torch.tensor(tokenizer.encode(prompt)).unsqueeze(0)

model.eval();
```
